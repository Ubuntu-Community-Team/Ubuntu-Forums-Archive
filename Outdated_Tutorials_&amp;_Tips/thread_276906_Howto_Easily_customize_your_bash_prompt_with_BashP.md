---
title: "Howto: Easily customize your bash prompt with BashPromptUtil"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by lonepie on 2006-10-13
Greetings all! I recently put together a small program that you can use to simplify the process of customizing your bash prompt. I always got confused writing the escape sequences by hand, so I created this handy tool that converts a simplified string (from what I call the "wizard") into the escape sequences needed by bash. Along with this conversion, a preview is also generated so you can see what your prompt will look like!

I wrote this in C# using monodevelop, so you must have the Mono and gtk-sharp runtime libraries installed. Also, I'm fairly new to programming on Linux, so let me know if there are any problems with the program.

I've attatched a .deb of the program; you can also get the source from my Google Code SVN by using the following command: ```
svn checkout http://bunchafunk.googlecode.com/svn/trunk/bashpromptutil/ bashpromptutil
``` 

To install using the attatched file, execute the following in your command line:
```

cd /download/dir
tar zxvf bashpromptutil_1.0b-1_i386.tar.gz
sudo dpkg -i bashpromptutil_1.0b-1_i386.deb

```

To compile and install the source from the svn repository, assuming you've checked out the code, execute the following: (tested and working with automake-1.9, but not working with automake-1.4)
```

cd /downloaddir/bashpromptutil
./autogen.sh (note if you want to install in somewhere other than /usr/local, run ./configure with the --prefix argument)
make
sudo make install

```

Once you have the program installed, run it by typing "bashpromptutil" at your command prompt or by using ALT+F2. The user interface is fairly simple to understand: you construct your bash prompt with the simplified syntax in the "(Wizard Input)" box. To insert a color or item, go to the "Wizard" menu to select one. The item will then appear in the "Wizard" box, in the form: {color} or <item>. You can also input regular characters or strings, for example the @ sign in: ```
<username>@<hostnameS>
```
Here is an example of the syntax you would use in the wizard:
```
{color1}<item1><item2> {color2}- {color3}<item3>{default}<item4> 
``` In english: items 1 and 2 will be color1, the "-" will be color2, item3 will be color3, and item4 will have the default color. Note you should always end with the default color to prevent your whole command line from being colored.

If you are satisfied with how the prompt looks, you can make the changes permanent by adding the following to your /home/*user*/.bashrc file:
```

#
PS1="output from bashpromptutil"

```*thanks HAARP*
(Make sure to comment out any other places in .bashrc where PS1 is set/assigned)

If you have any questions or comments, let me know!
Enjoy!

Note: if you do not have the Mono runtime installed, you can get it from the Ubuntu apt repository using Synaptic. You may have to have the universe and multiverse repos enabled in your sources.list.

---

### Post by lonepie on 2006-10-15
bump

---

### Post by HAARP on 2006-10-15
Wow, that looks promising. I'm definately going to try that out tomorrow
Thanks for your effort :)

edit: Try adding the required packages to the dependencies of your package. Use **--requires="package1, package2"** to the options of checkinstall


edit2: To use your custom bash prompt, add this to **/home/*user*/.bashrc**

```
# set custom prompt
PS1="output from bashpromptutil"
```

---

### Post by hikaricore on 2006-10-15
> [hikaricore@devistate:/media/devistate (493.4 Mb)]$ bashpromptutil
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory.

even installed mono myself, maybe I missed something *runs off to look again*

**edit reinstalled Mono to no effect, then downloaded mscorelib.dll resulting in this:

***```

** ERROR **: file domain.c: line 663 (mono_init_internal): assertion failed: (mono_defaults.monotype_class != 0)
aborting...
Aborted

```
***

maybe i'm not awake enough for this yet lol

---

### Post by lonepie on 2006-10-15
> [hikaricore@devistate:/media/devistate (493.4 Mb)]$ bashpromptutil
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory. 

I did a search on google and found this as a possible solution:
```
 
cd /usr/lib/mono
$ sudo ln -s 1.0 2.0

```

Let me know how that works for you.. I've only tested my app on 2 ubuntu boxes.

---

### Post by HAARP on 2006-10-15
Install the package "monodevelop". It's got dozens of dependencies, but one of those is the package you need.

---

### Post by hikaricore on 2006-10-15
thanks for the tips, but after trying one then the other still getting all kinds of error dumps lol.  i'm awake now so i'm removing everything, then i'll (re)apt-get monodevelop and friends.

then i'm going to build bashprmptutil instead of using the debian package.  hopefully i'll have better results to post in a minute :)

**update**

reinstalled monodevelop (and all suggested/dependancies)

```
sudo apt-get install monodevelop monodevelop-boo monodevelop-java monodevelop-nunit monodevelop-versioncontrol monodevelop-query nemerle libgdiplus
```

then tried autogen.sh from the svn then got:

```
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gmcs... no
configure: error: **gmcs** Not found
[hikaricore@hikaricore:/media/devistate/tmp/bashpromptutil (.1 Mb)]$ sudo apt-get install **mono-gmcs**

```

finally autogen.sh completes and i can **make && sudo make install**, goes well until:

```

error CS0006: Cannot find assembly `/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll'
Log:

Compilation failed: 33 error(s), 0 warnings
make[1]: *** [bin/Release/bashpromptutil.exe] Error 1
make[1]: Leaving directory `/media/devistate/tmp/bashpromptutil/bashpromptutil'
make: *** [all-recursive] Error 1
[hikaricore@hikaricore:/media/devistate/tmp/bashpromptutil (.2 Mb)]$ ls /usr/lib/mono/gtk-sharp-2.0/glib-sharp.dll
[COLOR="Red"]/usr/lib/mono/gtk-sharp-2.0/glib-sharp.dll    [/COLOR]
```

so it looks like i'm cursed :P  the file exists and make fails due to a missing file that's obviously there.. rofl   there's also about half a page listing every other dll file which is there, i just didn't want to flood this post with them all :)  ](*,) 

sorry to fill up your thread with bad karma :/

---

### Post by lonepie on 2006-10-15
```
sudo apt-get install gtk-sharp2
```

I'm sorry you're having so many problems, I hope this will do it...

---

### Post by hikaricore on 2006-10-15
Thank you I forgot to reinstall gtk-sharp2, apt didn't remove the files, but it wasn't installed..odd, but yet again I have the same result.  Tried to install the debian package again just incase but that dies too.

```
** (bashpromptutil.exe:23245): WARNING **: The following assembly referenced from /usr/local/lib/bashpromptutil/bashpromptutil.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.8.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/local/lib/bashpromptutil/).


** (bashpromptutil.exe:23245): WARNING **: The class Gtk.Window could not be loaded, used in gtk-sharp, Version=2.8.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f

** ERROR **: file class.c: line 2505 (mono_class_setup_parent): should not be reached
aborting...
Aborted

```

Nothing you or anyone can really do about this, there seems to be a serious issue with gtk-sharp on my system.  I'll try and install this on one comps at work tomorrow to see if it works there.  Good job on this tho :)  looks really nice, i think i'm just stuck editing my .bashrc manually.

Thanks again for the help.

---

### Post by lonepie on 2006-10-15
I'm sorry, let me know if it runs at work -- just hoping I didn't mess up somewhere to make it so this works for me and nobody else...

---

### Post by hikaricore on 2006-10-15
Not your fault.  I'm sure it's just me hehe, i'll let you know tomorrow, i have a fresh install of ubuntu on an old dell edge server so there shouldn't be any conflicts which are more than likely on mine.

---

### Post by hikaricore on 2006-10-16
jsut wanted to give you and update.  it works just fine on the ubuntu system i have setup fresh at work, so my guess is a hacked an update package somewhere along the line on my system that's giving me fits.  good work :)  i'll figure out my issue eventually hehe.

and thanks for all the help, even tho it was me all along

---

### Post by lonepie on 2006-10-16
glad to hear it worked!

---

### Post by kigol on 2007-07-04
pretty cool

---

### Post by Lunar_Lamp on 2007-07-07
Thanks, this was really helpful!  I've kept meaning to code something like this myself, but you've saved me the trouble!  Really appreciate your effort on this one, as I too have had problems with escaping chars previously.

---

