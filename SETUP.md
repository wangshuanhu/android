  
If you want to start help developing ownCloud please follow the [contribution guidelines][0] and observe these instructions:
  
### 1. Fork and download android/develop repository:

NOTE: You must have git in your environment path variable to perform the next operations.
  
* Navigate to https://github.com/owncloud/android, click fork.
* Clone your new repo: "git clone git@github.com:YOURGITHUBNAME/android.git"
* Move to the project folder with "cd android"
* Checkout remote develop branch: "git checkout -b develop remotes/origin/develop"
* Pull changes from your develop branch: "git pull origin develop"
* Make official ownCloud repo known as upstream: "git remote add upstream git@github.com:owncloud/android.git"
* Make sure to get the latest changes from official android/develop branch: "git pull upstream develop"

At this point you can continue using different tools to build the project. Section 2, 3 and 4 describe some of the existing alternatives.  

### 2. Building with Ant:
  
NOTE: You must have the Android SDK 'tools/', and 'platforms-tools/' folders in your environment path variable.

* Complete the setup of project properties and resolve pending dependencies running "setup_env.bat" or "./setup_env.sh" .
* Run "ant clean" .
* Run "ant debug" to generate a debuggable version of the ownCkoud app.

### 3. Building with console/maven:

NOTE: You must have mvn (version >= 3.1.1) in your environment path. Current Android 'platforms-tools' need to be installed.

* Download/install Android plugin for Maven, then build ownCloud with mvn:
* "cd .."
* "git clone https://github.com/mosabua/maven-android-sdk-deployer.git"
* "cd maven-android-sdk-deployer"
* "mvn -pl com.simpligility.android.sdk-deployer:android-19 -am install"
* "cd ../android/oc_framework"
* "mvn install"
* "cd .."
* Now you can create ownCloud APK using "mvn package"

### 4. Building with Eclipse:

NOTE: You must have the Android SDK 'tools/', and 'platforms-tools/' folders in your environment path variable.

* Complete the setup of project properties and resolve pending dependencies running "setup_env.bat" or "./setup_env.sh" .
* Open Eclipse and create new "Android Project from Existing Code". Choose android/actionbarsherlock/library as root.
* Clean project and compile.
* If any error appear, check the project properties; in the 'Android' section, API Level should be greater or equal than 14.
* Make sure android/actionbarsherlock/library/bin/library.jar was created.
* Create a new "Android Project from Existing Code". Choose android/oc_framework as root.
* Clean project and compile.
* If any error appear, check the project properties; in the 'Android' section, API Level should be 19 or greater.
* Make sure android/oc_framework/bin/classes.jar was created.  
* Import ownCloud Android project.
* Clean project and compile.
* If any error appears, check the project properties of owncloud-android project; in the 'Android' section:
  - API Level should be 19 or greater.
  - Two library projects should appear referred in the bottom square: actionbarsherlock/library and oc_framework. Add them if needed. 
* After those actions you should be good to go. HAVE FUN!

NOTE: Even though API level is set to 19, APK also runs on older devices because in AndroidManifest.xml minSdkVersion is set to 8.

### 5. Create pull request:
  
NOTE: You must sign the [Contributor Agreement][1] before your changes can be accepted!

* Commit your changes locally: "git commit -a"
* Push your changes to your Github repo: "git push"
* Browse to https://github.com/YOURGITHUBNAME/android/pulls and issue pull request
* Click "Edit" and set "base:develop"
* Again, click "Edit" and set "compare:develop"
* Enter description and send pull request.


[0]: https://github.com/owncloud/android/blob/master/CONTRIBUTING.md
[1]: http://owncloud.org/about/contributor-agreement/
