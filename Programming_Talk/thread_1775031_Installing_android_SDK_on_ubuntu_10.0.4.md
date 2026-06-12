---
title: "Installing android SDK on ubuntu 10.0.4"
date: 2011-06-04
forum: Programming Talk
---

### Post by alex_goacross on 2011-06-04
Hi! I'm trying to install android SDK on ubuntu!
Here is what i did:
1.I down the sdk(1.6) start package form the link:[http://xiaogui.org/android/docs/sdk/older_releases.html](http://xiaogui.org/android/docs/sdk/older_releases.html)
2.Unzip the download zip file and put it to my home folder
3.Down eclipse for ubuntn and integrate the adt plun-in form eclipse.org

Every thing seems Ok so far, so I want to set Android SDK in eclipse.
Navigate to Window->Preference->Android->Android SDK location,
I tried to choose the folder which i unziped folder, but seems the eclipse could not find the corrent SDK version or some thing, it just can't response the OK click..
SO I rechecked the SDK folder,and noticed that there is no a folder named platform-tools..

During the installation process, the most unsure thing is that:when I set up android SDK on windowx, I have to down all SDK stuff by SDK Manager.exe  from google, but there is no
one command like the skd manager on ubuntu..
So I think the SDK is not installed correct..

Thanks in advanced!
alex

---

### Post by ThatCoolGuy220 on 2011-06-04
hope u get an answer I wanna know this too I have an x10 mini 

it would be interesting

---

### Post by m_duck on 2011-06-04
Fire up a terminal and cd to the tools directory, within the android sdk directory (obviously adjusting the following for where your android sdk directory is):```
cd ~/.android-sdk/tools
```
Run the command 'android' in the terminal:```
android
```
Go to 'Available Packages' on the left. In what is now in the right hand side of the window expand the 'Android Repository' option and select (check the box) 'Android SDK Tools' and 'Android SDK Platform-tools' and install them.

I think that's pretty much the method anyway.

---

### Post by alex_goacross on 2011-06-04
> **m_duck said:**
> Fire up a terminal and cd to the tools directory, within the android sdk directory (obviously adjusting the following for where your android sdk directory is):```
cd ~/.android-sdk/tools
```
Run the command 'android' in the terminal:```
android
```
Go to 'Available Packages' on the left. In what is now in the right hand side of the window expand the 'Android Repository' option and select (check the box) 'Android SDK Tools' and 'Android SDK Platform-tools' and install them.

I think that's pretty much the method anyway.
Hi!m_duck,thanks for your response!
I tried What you show me and I got message below:
-----------------------------
XML verification failed for [http://dl-ssl.google.com/android/repository/repository.xml](http://dl-ssl.google.com/android/repository/repository.xml).
Error: cvc-elt.1: Cannot find the declaration of element 'sdk:sdk-repository'.
Failed to fetch URL [http://dl-ssl.google.com/android/repository/repository.xml](http://dl-ssl.google.com/android/repository/repository.xml), reason: Unknown
-----------------------------
By the way, I selected the setting/Misc/Force Https:// box checked! I got nothing if it does not select.

Message was edited by alex at 21:06 pm on 06/04/11.

---

### Post by SevenMachines on 2011-06-04
> **alex_goacross said:**
> XML verification failed for [http://dl-ssl.google.com/android/repository/repository.xml](http://dl-ssl.google.com/android/repository/repository.xml).
Error: cvc-elt.1: Cannot find the declaration of element 'sdk:sdk-repository'.
Failed to fetch URL [http://dl-ssl.google.com/android/repository/repository.xml](http://dl-ssl.google.com/android/repository/repository.xml), reason: Unknown


Its an old version of sdk tools error, you're using an outdated one, get the new one and it should work
[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

---

### Post by alex_goacross on 2011-06-04
> **SevenMachines said:**
> Its an old version of sdk tools error, you're using an outdated one, get the new one and it should work
[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Thanks Seven!
I'm afraid I could not link the site!
Any site like android.com or androidappdocs.appspot.com
is not available for me,even the andorid official web site..
I do not know what wrong with android official webs.


Message was edited by alex at 22:04 on 06/04/11.

---

### Post by SevenMachines on 2011-06-04
Sounds like you have much bigger problems! developer.android.com is *the* resource for android development. You might want to look for mirrors that work for you or sort out the problem with accessing the android developer website

---

### Post by alex_goacross on 2011-06-04
> **SevenMachines said:**
> Sounds like you have much bigger problems! developer.android.com is *the* resource for android development. You might want to look for mirrors that work for you or sort out the problem with accessing the android developer website
Maybe I could not fix this problem..
It's a network limitation policy i think,
especially in c-h-i-n-a!

Maybe I should look for mirrors for DEV ANDROID.

Thank you,anyway!

Message was edited by alex at 22:30 pm on 06/04/11.

---

### Post by SevenMachines on 2011-06-04
I see some people with similar filter-based problems have had some success with
[http://androidappdocs-staging.appspot.com/sdk/index.html](http://androidappdocs-staging.appspot.com/sdk/index.html)

---

### Post by alex_goacross on 2011-06-04
> **SevenMachines said:**
> I see some people with similar filter-based problems have had some success with
[http://androidappdocs-staging.appspot.com/sdk/index.html](http://androidappdocs-staging.appspot.com/sdk/index.html)

Another unavailable page for me!!:(
Thank you so much for your replies!

---

### Post by ThatCoolGuy220 on 2011-06-04
I can access to that page maybe you should need to use a proxy:

[http://www.hidebrowsing.com/](http://www.hidebrowsing.com/)

[http://www.hidemyass.com/](http://www.hidemyass.com/) ------> Sorry if this one is too offensive

---

### Post by alex_goacross on 2011-06-09
> **SevenMachines said:**
> Sounds like you have much bigger problems! developer.android.com is *the* resource for android development. You might want to look for mirrors that work for you or sort out the problem with accessing the android developer website

Yes, I finally find a http proxy site to access the android developer site and fix the problem.It's the problem of my SDK version.

Thanks all who have have a look on it!
Message was edited by alex at 22:06 pm on 06/09/11.

---

### Post by alex_goacross on 2011-06-09
> **ThatCoolGuy220 said:**
> I can access to that page maybe you should need to use a proxy:

[http://www.hidebrowsing.com/](http://www.hidebrowsing.com/)

[http://www.hidemyass.com/](http://www.hidemyass.com/) ------> Sorry if this one is too offensive

Yes, the first site works for me.
Thank you ThatCoolGuy220.:)

---

