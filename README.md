![enter image description here](https://raw.githubusercontent.com/omernaser/Huawei-MAP/master/huaweiicon.png)
### Setup

-   Available on NuGet:  [[https://www.nuget.org/packages/Xamarin.Android.HMSPushKit/](https://www.nuget.org/packages/Xamarin.Android.HMSPushKit/)] [![NuGet](https://camo.githubusercontent.com/8a3005d7f8ce0d50737ec134a48480ad61bfa5b9/68747470733a2f2f696d672e736869656c64732e696f2f6e756765742f762f506c7567696e2e4669726562617365507573684e6f74696669636174696f6e2e7376673f6c6162656c3d4e75476574)](https://www.nuget.org/packages/Xamarin.Android.HMSPushKit/)
-   Install into your .NETStandard project and Client projects.

**Platform Support**
Xamarin.Android

## Features

-   Receive firebase push notifications
-   Subscribing/Unsubcribing to topics
-   Support for push notification category actions
-   Customize push notifications

![enter image description here](https://raw.githubusercontent.com/omernaser/Huawei-PushKit/master/Screenshot_20200519_141028_com.companyname.hms_map_demo.jpg)

***

## > How To use the Push Kit

###  Create an application with AppGallery Connect
To run demo application you need to follow the steps specified under the item 1(**Configuring App Information in AppGallery Connect**), in the URL below.
- [Push Kit App Development Preparations](https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/Preparations#h1-1575707195634)
- **Note:** You can follow ***2.10 Create a signature file*** section of this document to create keystore file.

###  Place your agconnect-services.json file inside the project
Download the **agconnect-services.json** file created for your AppGallery application, by following the steps specified under the item 1.4, in the URL below.
- [Push Kit App Development Preparations](https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/Preparations#h2-1575707405416)

Once you download your "**agconnect-services.json**" file, place it under the "Assets" folder of the demo project.

###  Open the demo project and modify AndroidManifest.xml
Open up Visual Studio 2019. Then from the menu;
- Click "Open a project or a solution"
- Navigate to the directory where the demo project resides and open "XamarinHmsPushDemo.csproj".

Open the "AndroidManifest.xml" file under the "Properties" folder. Then change the "package" property with package name you specified on the AppGallery Connect platform.

###  Create a signature file
If you already have a signature file generated, you can skip to the next step.

If you don't have a signature file, perform the following steps:
- Open the command line tool (using the **cmd** command) and run the **cd** command to go to the directory where **keytool.exe** is located under the **JDK** installation directory. 

    **Note:** Visual Studio comes with OpenJDK installed.

- Run the following command:

```
keytool -genkey -keystore <keystore-file> -storepass <keystore-pass> -alias <key-alias> -keypass <key-pass> -dname <dname> -keysize 2048 -keyalg RSA -validity <validity-period>
```

- In the preceding command;

    - **\<keystore-file\>** is the complete path to the app's signature file. File extension must be .jks or .keystore. For example; "D:\Android\keystore.jks"
    - **\<keystore-pass\>** is the password of your keystore. Requires minimum 6 characters. For example; "123456"
    - **\<key-alias\>** is the alias name of key that will be stored in your keystore. For example; "pushkitdemo"
    - **\<key-pass\>** is the password of your key. Requires minimum 6 characters. For example; "12345"
    - **\<dname\>** is a unique identifier for the application in the keystore. For example; "o=Huawei"
    - **\<validity-period\>** Amout of days the key will be valid with this keystore. For example; "36500"

    Example:
```
keytool -genkey -keystore D:\Android\keystore.jks -storepass 123456 -alias pushkitdemo -keypass 123456 -dname "o=Huawei" -keysize 2048 -keyalg RSA -validity 36500
```

###  Sign your application
You need to sign your application in order to be able to register & use your signature file in the AppGallery Connect platform. Perform the following steps:
- In the "Solution Explorer" window, right click the demo and open "Properties"
- In the window that just opened, select "Android Package Signing" from the menu on the left.
- Check the option "Sign the .APK file using the following keystore details.". Then fill out the form below with required information.

    **Note:** You should perform these steps for both **Debug** and **Release** configurations.

###  Obtaining the SHA-256 fingerprint from signature file
You need to obtain the SHA-256 Fingerprint of your signature file.

Perform the following steps:
- Open the command line tool (using the **cmd** command) and run the **cd** command to go to the directory where **keytool.exe** is located under the **JDK** installation directory. 

    **Note:** Visual Studio comes with OpenJDK installed.

- Run the following command and copy the SHA-256 fingerprint from the result.

```
keytool -list -v -keystore <keystore-file>
```
- In the preceding command;
    - **\<keystore-file\>** is the complete path to the app's signature file. For example; "D:\Android\mykeystore.jks"

    Example:
```
keytool -list -v -keystore D:\Android\keystore.jks
```

### Registering the singing certificate fingerprint
The signature fingerprint should be registered on the AppGallery Connect platform.

Perform the steps below:
- Sign in to [AppGallery Connect](https://developer.huawei.com/consumer/en/service/josp/agc/index.html), click "**MyApps**" then select your application.
- From the menu on the top, click on "**Develop**" and scroll to the bottom of the page.
- Set the SHA-256 certificate fingerprint as the SHA-256 fingerprint you copied in the previous step.

### Run & debug your application
You can now run your application and it should automatically start up on your mobile device.

***

## Reference

 - [https://developer.huawei.com/consumer/en/hms/huawei-pushkit](https://developer.huawei.com/consumer/en/hms/huawei-pushkit)
   
   [https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/push-introduction](https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/push-introduction)
   
   [https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/push-use-cases](https://developer.huawei.com/consumer/en/doc/development/HMS-Guides/push-use-cases)
   [https://developer.huawei.com/consumer/en/codelab/HMSPushKit/index.html#4](https://developer.huawei.com/consumer/en/codelab/HMSPushKit/index.html#4)
