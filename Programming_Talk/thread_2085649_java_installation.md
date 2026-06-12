---
title: "java installation"
date: 2012-11-18
forum: Programming Talk
---

### Post by antobbo on 2012-11-18
Hi all, I have installed java on my computer as well as netbeans, but I have just noticed that I don't have the documentation, not entirely sure why. The folder - see attachment - doesn't have the documentation folder in it. COuld anybody kindly tell me how and where I get it from please?
thanks

---

### Post by 3246251196 on 2012-11-18
> **antobbo said:**
> Hi all, I have installed java on my computer as well as netbeans, but I have just noticed that I don't have the documentation, not entirely sure why. The folder - see attachment - doesn't have the documentation folder in it. COuld anybody kindly tell me how and where I get it from please?
thanks

Maybe

```
sudo apt-cache search jdk | grep documentation
```

Will provide a reference to one of the packages you need.

---

### Post by Unterseeboot_234 on 2012-11-18
Per your screen capture I think you've got it. That src.zip archive is the one NetBeans uses (and it usually is found by default). That zipped api doc is the code-completion feature.

You can also link to the online api docs using in NetBeans Tools -> Java Platforms [TAB] JavaDoc [Button] Add URL
[http://download.oracle.com/javase/7/docs/api/](http://download.oracle.com/javase/7/docs/api/)

or download the actual arhive as a zip (it also will be src.zip) and link in the same Dialog window.

So, that should help you if you were wanting code-completion feature. I keep a bookmark to the Oracle API docs to view in my browser for reference.

---

### Post by slickymaster on 2012-11-19
There's yet another possibility. Netbeans has a plugin called Netbeans API Documentation wich includes a complete copy of the NetBeans API documentation for offline browsing and Javadoc index searching. It covers all of the official API modules plus some APIs considered under development.

To install it you just have to go under **Tools > Plugins > Available Plugins** and select it for install.

---

### Post by antobbo on 2012-11-19
thanks all for the suggestion.
Unfortunately I haven't mentioned the fact that I don't know anything about java, I have just started to learn it
@3246251196 would this ```
sudo apt-cache search jdk | grep documentation 
```install all the documentation I need?

@Unterseeboot_234: I read there should be another folder in there in addition to what's there already. I have visited [http://download.oracle.com/javase/7/docs/api/](http://download.oracle.com/javase/7/docs/api/) before, but can't find a download option?!


@slickymaster. I have found the option, but which plug in should I select?
thanks

---

### Post by slickymaster on 2012-11-19
Regarding the API documentation, the download link is [this]("http://www.oracle.com/technetwork/java/javase/documentation/java-se-7-doc-download-435117.html"). Don't forget you have to click on the Accept License Agreemen radio button.

Regarding the Netbeans plugin, you have to select the one called **_Netbeans API Documentation_**. They are sorted alphabetically, so you just have to scroll down to the letter 'n'.
If you're having trouble installing the plugin, you can always download it from the NetBeans Plugin Portal, [here]("http://plugins.netbeans.org/PluginPortal/").

---

### Post by slickymaster on 2012-11-19
In order to help you, here's a PrtScn of the plugin.

---

### Post by antobbo on 2012-11-20
fabulous, thanks. I am downloading the API first: once downloaded do I need to extract it or place it as it is in the jdk1.6.0_37 folder?

ABout the netbean plugin, is it essential that I download it or can I do without it?
thanks

---

### Post by slickymaster on 2012-11-20
Regarding the Java API documentation you don't have to extract it. Just download it and place in a folder of your choice. Then, in Netbeans, just go under **Tools > Java Platforms** and in the Java Platform Manager select the Javadoc Tab, click on the Add Zip Folder and navigate to the folder where you placed the downloaded Java API documentation.
In my case, I also added the link to the online URL of the Java API documentation.

For the Netbeans API documentation, it's your choice, either install it or not. But it isn't a heavy plugin, just 13 MB, so I don't see why wouldn't you use it.

I'm uploading two images in order to help you to get things done.

If you'll need some more help, just post it. If you think you're done with this thread don't forget to tag it as SOLVED.

---

### Post by antobbo on 2012-11-21
Thanks, I am going through the java api zip folder documentation now. I have done all you said, and now I have 2 folders as in the screenshot, is it ok? Is the position of the folders ok?
thanks

---

### Post by slickymaster on 2012-11-21
Yes, the position is alright. The only thing I would point you is that you have downloaded the Java SE Development Kit 7 Documentation and added the link to the online URL of the Java Platform Standard Edition 6.

Why don't you replace that URL to match the version of the one you've download? If you want the URL for it it's [http://download.oracle.com/javase/7/docs/api/](http://download.oracle.com/javase/7/docs/api/) you just have to replace this for the one you have.

Another thing, and this is just a particularity, nothing more, is because you position the URL first, and the Zip package after, whenever you'll need to consult Javadocs the IDE will firstly call upon the online URL and only if it fails to connect to the site it will call upon your Zip package on your computer.
If it were the other way around, the IDE would first call locally upon the Zip package and only if it doesn't manage to do it, by any package corruption, or because it's been moved or deleted, only then it will call upon the online version.

---

### Post by slickymaster on 2012-11-21
Take a look at the way I place them, just for curiosity. I first have the Zip package and afterwards the URL option.

---

