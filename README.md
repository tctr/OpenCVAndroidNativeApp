# **OpenCV Android Sample Project With Native App (C++ dev)**

## **First steps**

- How to create an **android native app** with **OpenCV** and **C++**

- Starting from a **Native C++** new project in **Android Studio 4.0.0** (28/05/2020)

- Example taken from :
  - https://youtu.be/Sn3YhfY5jqg
  - https://www.thecodingnotebook.com/2020/04/image-processing-with-opencv-in-android.html

- Needed to downgrade Android SDK Build tools from 33.0.2 to 29.0.2 to build the project

- Structure of the native app :

![Native App Structure](./DocsImgs/NativeAppStructure.png "Native App Structure")

## **Add the CPP code**

- Add the .h and .cpp files where you have your own cpp code

- Change CMakeList.txt to add OpenCV-Android-SDK

- Now you should see opencv2 includes in the Android view of the project **You may have to close the project and open it to see it**

![OpenCV includes in Android Studio](./DocsImgs/AndroidStudioWithOpencvIncludes.png "OpenCV Includes")

## **Build the GUI of our app in Java**

- After entering c++ code in opencv-utils.cpp and native-app.cpp  go to res => layout => activity_main.xml and remove "HelloWorld"

![Remove HelloWorld from Layout](./DocsImgs/RemoveTextInLayout.png "Activity Layout")

- Then go under project view and res => New Android Resources to create a new folder in **Res**

![Open Android Resource Directory](./DocsImgs/OpenAndroidResourceDir.png "Android Resource Dir")

- For this select **drawable** in resource type, then select **density** with **no density** 

![Select Density](./DocsImgs/selectResDensity.png "Select Density")

![No Density](./DocsImgs/NoDensity.png "No Density Folder")

- Which adds a new folder **drawable-nodpi**

![No-dpi folder](./DocsImgs/drawable-nodpi-folder.png "drawable-nodpi Folder")

- Then :
  - drop an image in the **drawable-nodpi** folder
  - go to common => ImageView
  - drop the img on the layout
  - arrange the image size and position

![image_on_layout](./DocsImgs/image_on_layout.png "Image on Layout")
  
## **Functions on Java side with MainActivity.kt**
- Import all the necessary packages :
  - android.graphics.Bitmap
  - android.graphics.BitmapFactory
  - android.view.View
  - android.widget.Seekbar
  - java.lang.Float.max

![Package Imports](./DocsImgs/packages_import.png "Packages Imports in MainActivity.kt")

- Declares the new native (JNI) methods in MainActivity.kt

![Native Methods declared](./DocsImgs/declare-native-methods.png "Declare Native methods in MainActivity.kt")

- Processing Android Bitmap

  - on Creation : load the image in srcBitmap and dstBitmap, set the imageView to dstBitmap as it will be updated

  ![Load image](./DocsImgs/load_img_and_set_imageView.png "Load image in MainActivity.kt")

  - Add the methods applied when changes occur in the seekbar and the button 

  ![Seek bar change](./DocsImgs/seekbar_method.png "Seekbar change in MainActivity.kt")

  ![Button change](./DocsImgs/button_method.png "Button change in MainActivity.kt")

## **Modifications on the APK generation**
- To avoid having the libs compiled for all architectures => use the **split** option  in **build.gradle**

  ![split option](./DocsImgs/split_option.png "Slit APKs option in build.gradle")

- Build a **signed** APK in Release config => modifications in **build.gradle**

  ![Signing option](./DocsImgs/signing_release_apk.png "APK Signing option for Release config in build.gradle")
