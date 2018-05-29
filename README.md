# 项目中文介绍

Android 7.0中google改变了对证书的信任方式,确切的说是android 7.0不再信任用户自己安装的CA证书,这导致我们使用抓包工具(Charles/Fiddler等)抓取HTTPS流量时,无法再使用中间人攻击的方式进行,但是google也给出了解决方案,就是app的开发人员可以自己更改app中的安全设置,从而可以调试自己的应用,显然这样的方案只适用于该应用的开发人员.这个项目则是通过对apk文件重新签名达到可以抓取任意app的HTTPS流量.

# Add Security Exception to APK

In Android 7.0, Google introduced changes to the way user Certificate Authorities (CA) are trusted. These changes prevent third-parties from listening to network requests coming out of the application:
More info: 
1) https://developer.android.com/training/articles/security-config.html
2) http://android-developers.blogspot.com/2016/07/changes-to-trusted-certificate.html

This script injects into the APK network security exceptions that allow third-party software like Charles Proxy/Fiddler to listen to the network requests and responses of some Android applications.


## Getting Started

Download the script and the XML file and place them in the same directory.

### Prerequisites
APKTOOL is not needed anymore.

~~You will need `apktool` and the Android SDK installed~~

~~I recommend using `brew` on Mac to install `apktool`:~~

~~```brew install apktool```~~

## Usage

The script take two arguments: 
1) APK file path.
2) keystore file path (**optional** - Default is: ~/.android/debug.keystore )

### Examples

```
./addSecurityExceptions.sh myApp.apk

or

./addSecurityExceptions.sh myApp.apk ~/.android/debug.keystore

```
