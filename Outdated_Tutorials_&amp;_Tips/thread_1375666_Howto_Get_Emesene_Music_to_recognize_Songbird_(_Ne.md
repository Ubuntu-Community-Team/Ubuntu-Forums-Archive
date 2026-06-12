---
title: "Howto: Get Emesene Music to recognize Songbird ( New )"
date: 2010-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by phDaemon on 2010-01-08
Ok, so i looked around this forum, and google, and found no way of doing this. The one site that offers the (old) way to do this is in italian, and even for me (im spanish) it was hard to translate, so for Ubuntu Karmic (9.10 All Arcs) and Songbird 1.4.3 im going to be showing you how i got it working.

Download the attached files ( I got the patch from [The Italian Site]("http://maurolinux.wordpress.com/2008/12/22/plugin-mostracanzone-di-emesene-con-songbird-10-perche-no/") ) and modified the DBUS extension to work with the new Songbird, at the bottom of this post.

( You MUST have the **CurrentSong** plugin **installed** in emesene for this tutorial to work! )

1. Close emesene.
2. **Extract** the files ( right click -> extract here ) and extract the Patch file
3. Then **install** the songbird extension -> restart songbird. ( Otherwise it will not register inside emesene )
4. **Copy** the patch file over to your emesene directory and _**change to that directory**_.

```

sudo cp currentsong_songbird.patch /usr/share/emesene/plugins_base/currentSong/
cd /usr/share/emesene/plugins_base/currentSong/

```or 

```

sudo cp currentsong_songbird.patch ~/emesene/plugins_base/currentSong/
cd ~/emesene/plugins_base/currentSong/

```or _anywhere else you have it installed_.

The tutorial on the site tells you to do some commands that error out.
**_These are the commands you need to do_**:

```

sudo patch -p0 -i currentsong_songbird.patch

```[COLOR=Red]**[COLOR=Black]choose [/COLOR]__init__.py**[/COLOR] (it WILL ERROR OUT ) but **creates Songbird.py** inside that directory.
You will need to edit the __init__.py file yourself, because the patch fails in doing so.

```

sudo gedit __init__.py

```[B][COLOR=Red]
ADD[/COLOR][/B] this
```

    from Songbird import Songbird

```[B][COLOR=Red]
AFTER[/COLOR][/B] this line
```

    from Xmms import Xmms

```After you have accomplished this, finish by doing the following:
1. Open emesene.
2. Make sure the musicsong plugin is [COLOR=Red]**ON**[/COLOR].
3. Click on "**No Media Playing**" and select songbird from the list of music players.

If songbird is already running, it should say Status: **running**. Click Ok.
If songbird is not started, start it, select a song, and verify that it says Status: **running**.

Please post if this was useful to you or if you need any help, or if i made a mistake.

Thank you! And enjoy your music!
EDIT: The extension included in the main download is for 64bit systems. So if you have a 32 bit system, **ALSO** download the 32 bit version attached here.

---

### Post by phDaemon on 2010-01-08
A little bit to add,
Screenshot of it working under Karmic (my desktop)

---

### Post by FDrico on 2010-01-10
I think i did everything you say i should do to get CurrentSong working with Songbird. But something doesn't let me activate the option.

When I open Emesene, after doing what you say, i get this message:

> PLUGIN MANAGER: 
Exception importing CurrentSong
No module named Songbird

And the extension doesn't load.

Have you got any idea of what the problem is?

(Sorry for my english, i'm from Argentina)

---

### Post by FDrico on 2010-01-10
I think i did everything you say i shoul do to get CurrentSong working with Songbird. But something doesn't let me activate the opcion.

When I open Emesene, after doing what you say, i get this message:

> PLUGIN MANAGER: 
Exception importing CurrentSong
No module named Songbird

And the extension doesn't load.

Have you got any idea of what the problem is?

(Sorry for my english, i'm from Argentina)

---

### Post by phDaemon on 2010-01-11
Did you apply the patch? Check to see if there is a file named Songbird.py in the directory where the patch is.

also

when you do
```

sudo patch -p0 -i currentsong_songbird.patch

```

It will ask you which file you want to patch, even tho it should not matter since they are all named the same, type in

```

__init__.py

```

IT WILL ERROR out, but will create/patch Songbird.py
then you follow on with editing __init__.py

---

### Post by FDrico on 2010-01-11
I did everything again, and i found the problem. When i apply the patch, it doesn't create the Songbird.py on the same directory, but i creates a new folder inside it and places it there.

For example, it should create Songbird.py on
```
/usr/share/python-support/emesene/plugins_base/currentSong
```
But instead, it creates Songbird.py on
```
/usr/share/python-support/emesene/plugins_base/currentSong/plugins_base/currentSong
```

I just moved the file, and now, when i start Emesene, the CurrentSong plugin is running.

But it still doesn't work :(

I edited the __init__.py file with Gedit, and added the line you suggest after XMMS and then, i tried doing the same, but after the last line (XMMS2). None worked.

When i write it after XMMS (and before XMMS2), the status says "Unknown". When i write the line after XMMS2 (i mean, when i write it in the last place), the status says "Not Running", even when i open Songbird before and after running Emesene.

Oh, one more thing, maybe really important (i don't know): I have an i686 system, and the plugin for songbird is for x86_64.  I just edited the Install.rdf, so i was able to install it on my Songbird.

Thank you very much for you help.

---

### Post by phDaemon on 2010-01-11
Hmmm, its weird that it creates it in that directory, it worked fine on mine.

As far as the not running thing goes, im pretty sure its because its the wrong arc. Uploaded a 32 bit version, let me know if the problem still happens.

Download the file on this post, uninstall the previous extention and see if this one works for you.
```

    from Xmms import Xmms

```Thats where the patch wanted to do it, and thats where i did it on mine altough it should not make a diff so try it the way you have it now too
[B]
EDIT!!!: [/B]HEY I just saw your folder is 
```

/usr/share/python-support/emesene/plugins_base/currentSong/plugins_base/currentSong

```**[COLOR=Red]IT SHOULD BE[/COLOR]**
```

/usr/share/emesene/plugins_base/currentSong/

```NO **PYTHON-SUPPORT**
So copy it over to the correct folder!!
[B]
32bit version attached here:[/B]

---

### Post by FDrico on 2010-01-11
You're great. Thank you very much. I installed the 32bit version, and it worked just fine.

Right now, it's working perfectly.

About the folder, the directory

```
/usr/share/emesene/
```

doesn't exist. And copying everything and making new shortcuts wasn't exciting, you know ;) But it worked great, even when i didn't copy anything. It seems to me that the folder were Emesene is installed doesn't matter, or the folder where i have it installed works ok.

So, my problem was the version of the extension.

Thank you very much for you help and your time :D

---

### Post by xrecar on 2010-01-14
Thank You! Needed the DBusBird Plugin.

---

### Post by alekz on 2010-01-19
Great!

---

### Post by Toost Inc. on 2010-04-28
This is purely based on my own experience but when using Songbird 1.4.3, which doesn´t support the DBus Bird add-on anymore (it only goes up till 1.1.1). 
You could always edit the install.rdf file from the xpi but I found out that installing the [MPRIS add-on](http://addons.songbirdnest.com/addon/1626) worked for me as well. YMMV though...

---

