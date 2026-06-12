---
title: "Restricted Extras and mouse gestures"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Nightmist on 2012-07-19
Hello,

I have two quick questions after a fresh install of Ubuntu.

1. When trying to install the Ubuntu Restricted Extras, I got a message that I had to remove two libraries (don't remember specifics since I'm not at home now). But I was wondering if I need to install the restricted extras since I already checked off the option to install proprietary drivers (or something like that) during the Ubuntu installation?

2. I have installed mouse gestures both in Chrome and Firefox, but it doesn't work properly. When I press and hold the right mouse button to perform gestures, the context menu pops up already before I release the mouse button - and as such the gesture fails.

I am using Ubuntu 12.04 LTS.

---

### Post by mikewhatever on 2012-07-19
1. You don't. In case anything still needs a codec, Ubuntu will show a prompt.

2. Don't know anything about it. Sorry.

---

### Post by Nightmist on 2012-07-19
All right, then I won't bother with the packages.

Any word on why mouse gestures aren't working, though? If you try to right click in your web browser, does the context menu come up when you press down, or when you release the right mouse button?

---

### Post by bobsan on 2012-07-19
1. the removed one were crippled because of patent/legal reason, the ones that replace them in the restricted extra package are the fully functional ones. You should install the package, I don't understand mikewhatever's advice.

---

### Post by z3nhakr on 2012-07-19
> **bobsan said:**
> 1. the removed one were crippled because of patent/legal reason, the ones that replace them in the restricted extra package are the fully functional ones. You should install the package, I don't understand mikewhatever's advice.
 
+1 this. installing restricted extras will save time later on by installing all the codecs you'll need instead of having to install them one at a time as you require them.

what plugins are you using for gestures?

---

### Post by mikewhatever on 2012-07-19
> **bobsan said:**
> 1. the removed one were crippled because of patent/legal reason, the ones that replace them in the restricted extra package are the fully functional ones. You should install the package, I don't understand mikewhatever's advice.

The restricted extras package pulls in a good deal more then just codecs. You get java, ms-fonts, cab-extract, unrar and a bunch of libraries, which, IMHO, is an overkill.
To see what's going to be installed, without actually installing it, run 
"sudo apt-get -s install ubuntu-restricted-extras".
Now, you may ask, "What's the harm of having java and the rest installed?" Again, IMHO, java should be avoided if not needed, because it's a major security risk, and when installed through a matapackage, the user is often unaware that it's even there. As for the rest, I don't like installing stuff, knowing I'll never use it.

---

### Post by Nightmist on 2012-07-20
> **z3nhakr said:**
> +1 this. installing restricted extras will save time later on by installing all the codecs you'll need instead of having to install them one at a time as you require them.

what plugins are you using for gestures?

1. All right, I need java for banking services I believe, so I guess I'll install the restricted extras.

2. The plug-in is called "Gestures for Chrome(TM) Plus1.12.1.5". But the problem seem to be with how right clicking is handled. In Windows, if you press and hold right mouse button (RMB) no menu pops up before you release it; thus you can "paint" gestures without the context menu popping up. In Ubuntu the context menus pop up immediately the moment I press and hold RMB, not upone release, so I'm not able to "paint" the gesture.

---

### Post by stinkeye on 2012-07-20
> **Nightmist said:**
> 

2. The plug-in is called "Gestures for Chrome(TM) Plus1.12.1.5". But the problem seem to be with how right clicking is handled. In Windows, if you press and hold right mouse button (RMB) no menu pops up before you release it; thus you can "paint" gestures without the context menu popping up. In Ubuntu the context menus pop up immediately the moment I press and hold RMB, not upone release, so I'm not able to "paint" the gesture.

Try easystroke.
```
sudo apt-get install easystroke
```
Set up global gestures and/or gestures just for chrome.
Can bind spare mouse buttons to keys ,terminal commands to gestures or keys to gestures.
How to setup [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11").

---

### Post by bobsan on 2012-07-20
> **mikewhatever said:**
> The restricted extras package pulls in a good deal more then just codecs. You get java, ms-fonts, cab-extract, unrar and a bunch of libraries, which, IMHO, is an overkill.
To see what's going to be installed, without actually installing it, run 
"sudo apt-get -s install ubuntu-restricted-extras".
Now, you may ask, "What's the harm of having java and the rest installed?" Again, IMHO, java should be avoided if not needed, because it's a major security risk, and when installed through a matapackage, the user is often unaware that it's even there. As for the rest, I don't like installing stuff, knowing I'll never use it.

If you keep your java updated through the Ubuntu packaging system I don't see a problem with security. IMO its risk is vastly exaggerated. It has its use, maybe not for you, but others may need it. Moreover you can always uninstall it later (and libraries that you are sure that you don't need) if you don't want it with a sudo apt-get remove, or through synaptic. If you don't want the fonts just don't agree to the EULA, that is simple.

---

### Post by Nightmist on 2012-07-21
> **stinkeye said:**
> Try easystroke.
```
sudo apt-get install easystroke
```
Set up global gestures and/or gestures just for chrome.
Can bind spare mouse buttons to keys ,terminal commands to gestures or keys to gestures.
How to setup [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11").

Thanks. Easystroke made it work. After installing it, the context menu didn't pop up right away when pressing the right mouse button (which was button 3 in easystroke), so I had time to finish the gestures.

---

