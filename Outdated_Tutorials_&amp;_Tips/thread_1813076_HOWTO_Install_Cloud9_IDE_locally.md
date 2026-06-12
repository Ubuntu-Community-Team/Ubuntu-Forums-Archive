---
title: "HOWTO: Install Cloud9 IDE locally"
date: 2011-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by lovinglinux on 2011-07-27
In the last couple of days I have been playing with Cloud9 and it looks awesome. This tutorial will explain how to install Cloud9 IDE locally on your Ubuntu, how to create a script to easily switch between your projects and how to launch it using a customized separate browser profile.

[[IMG]http://www4.picturepush.com/photo/a/6181272/640/6181272.png[/IMG]](http://picturepush.com/public/6181272)

**What is Cloud9?**

[Cloud9]("https://github.com/ajaxorg/cloud9") is an open-source full browser-based IDE with team collaboration and online project hosting, through GitHub integration. 

For more information about it's functionality and innovative approach, see [**Why Cloud9 Deserves your Attention**](http://net.tutsplus.com/articles/why-cloud9-deserves-your-attention/).

If you just want to use Cloud9 in the cloud, create a free account at [http://cloud9ide.com]("http://cloud9ide.com") and jump to section 4 of this tutorial.

**1. Installation**

The installation instructions are based on [the tutorial posted on the Gratuitous Development blog]("http://gratdevel.blogspot.com/2011/03/setting-up-cloud9-on-ubuntu-1010-32-bit.html") and have been tested on Ubuntu 11.04.

*1.1 Installing Dependencies*

First you need to install the necessary dependencies to build [node.js]("http://en.wikipedia.org/wiki/Node.js") and [o3]("https://github.com/ajaxorg/o3").

Open a terminal, paste the following code and hit Enter:

```
sudo apt-get install -y build-essential g++ curl libssl-dev apache2-utils git libxml2-dev
```

*1.2 Installation directory*

In order to avoid permissions issues, it is recommended to create a folder under your home for installing the necessary applications. Furthermore, you need to install everything on the same directory, so I recommend a separate folder just for these applications. In my system, I install several applications manually in the *~/install* folder, so I have created another sub-folder for Cloud 9 stuff. For this tutorial I will use the same folder as the original tutorial, which will be *~/local*. However, you can use whatever name and directory structure you want, just make sure to use the correct paths in the commands throughout the tutorial. 

So, create the installation folder and add the *bin* sub-folder to bash:

```
mkdir ~/local

echo 'export PATH=$HOME/local/bin:$PATH' >> ~/.bashrc
. ~/.bashrc

```

Then cd into the installation directory. All the following instructions are assuming you started your terminal within the installation folder. They will instruct when you need to change directories.

```
cd ~/local
```

*1.3 Installing node.js*

The following commands will fetch the node.js source code from GitHub, cd into it's directory, switch to the latest stable branch, configure it to be installed in the *~/local* folder, build, install and test it.

```
git clone git://github.com/joyent/node.git
cd node
git checkout v0.4.10
./configure --prefix=~/local
make
make install
make test
cd ..
node -v
```

*1.4 Installing [npm]("http://npmjs.org/") (Node Package Manager)*

```
curl http://npmjs.org/install.sh | sh
npm -v
```


*1.5 Installing Cloud9*

The following commands will fetch Cloud9 source code from GitHub, cd into it's directory, switch to the latest development branch and update the submodules.

```
git clone git://github.com/ajaxorg/cloud9.git
cd cloud9
git checkout devel
git submodule update --init --recursive
bin/cloud9.sh
cd ..
```

*1.6 Installing o3*

The following commands will fetch o3 source code from GitHub, cd into it's directory, build it and copy it to cloud9 installation folder.

```
git clone http://github.com/ajaxorg/o3
cd o3
./tools/node_modules_build
cp build/default/o3.node ../cloud9/support/jsdav/support/node-o3-xml-v4/lib/o3-xml/
cd ..
```

That's it for the installation part.

*1.7 Removal*

In case you decide Cloud9 is not for you or if it doesn't work as expected, you can remove it completely by deleting the installation directory, which is ~/local in this tutorial.

Then open ~/.bashrc:

```
gedit ~/.bashrc 
```

Remove the following line:

```
export PATH=$HOME/local/bin:$PATH
```

To remove the dependencies:

```
sudo apt-get remove build-essential g++ curl libssl-dev apache2-utils git libxml2-dev
```


**2. Launching your project with Cloud9**

Cloud9 can be used with any web browser. All you need is to start the server with your project path:

```
~/local/node ~/local/cloud9/bin/cloud9.js -w ~/pathtoyourproject
```

Then you can open it in your browser by typing the following url in the address bar:

```
http://127.0.0.1:3000
```

To stop the server:

```
killall node
```


**3. Easily switching projects**

Unlike more traditional integrated development environments like Netbeans, Eclipse or Aptana, which allows to open several projects simultaneously, it seems Cloud9 is designed to work with a single project. I have several git projects under the same root directory and I tried to open the root instead of the project itself, but it doesn't seem to work as expected. You can actually do it, but then you lose git integration.

The single project approach makes sense for cloud hosting, but it is a little bit inconvenient when you are working with a local installation. However, it is easy to switch projects with a simply shell script.

First make sure you have zenity installed:

```
sudo apt-get install zenity
```

Then create/open the script with your favourite text editor:

```
gedit ~/local/projectswitcher.sh
```

Add the following code and save it

```

#!/bin/bash

PROJECT=$(zenity --file-selection --directory --title 'Select a Project Directory')

if test -d "${PROJECT}";then
  killall node
  $HOME/local/bin/node $HOME/local/cloud9/bin/cloud9.js -w ${PROJECT} &
fi
exit
```

Then make it executable:

```
chmod +x ~/local/projectswitcher.sh
```

To switch projects, launch the script by double-clicking *~/local/projectswitcher.sh* and select the project folder with the folder picker when prompted. Assuming Cloud9 is already opened in your browser (see previous section), just reload the page to switch to the new project.

You can add the scrip to your desktop or panel for convenience. If you are using Firefox, you can also use my [FoxRunner]("https://addons.mozilla.org/en-US/firefox/addon/foxrunner/") extension, that allows to run scripts from Firefox. This can be particularly useful for switching projects or if you use other scripts to manage your projects repositories. You can import the scripts above into FoxRunner or even create them using FoxRunner interface. For more information, see the [extension documentation]("http://www.webgapps.org/add-ons/foxrunner/documentation").

Here is a screenshot of FoxRunner sidebar along with Cloud9:

[[IMG]http://www1.picturepush.com/photo/a/6182539/640/6182539.png[/IMG]](http://picturepush.com/public/6182539)


**4. Create a separate browser profile**

Although you can open Cloud9 within your browser session, you might find more convenient to work with it as a standalone application. You can do that by simply using a different browser, but using a different profile allows you to use the same browser you like for regular browsing. A different profile will allow you to use a different set of add-ons, that are related to development, without cluttering your browser with more icons. It also allows to customize the browser appearance, independently from your default profile.

*4.1 Configuring a cloud9 browser profile in Firefox*

To create a new profile in Firefox, execute the following command:

```
firefox -no-remote -CreateProfile "cloud9"
```

If you want to start your profile from command-line use:

```
firefox -P -no-remote "cloud9" http://127.0.0.1:3000
```

You can also create a script to launch the profile:

```
gedit ~/local/firefox-profilelauncher.sh
```

Add the following code and save it:

```
#!/bin/bash

firefox -P -no-remote "cloud9" http://127.0.0.1:3000 &
exit
```

Make it executable:

```
chmod +x ~/local/firefox-profilelauncher.sh
```

To delete the profile, in case you are uninstalling everything, open the profile manager and delete the profile:

```
firefox -no-remote -P
```


*4.2 Configuring a cloud9 browser profile in Chrome*

To create/start a cloud9 profile in Chrome use:

```
google-chrome --user-data-dir=$HOME/.config/google-chrome/cloud9 http://127.0.0.1:3000
```

You can also create a script to launch the profile:

```
gedit ~/local/chrome-profilelauncher.sh
```

Add the following code and save it:

```
#!/bin/bash

google-chrome --user-data-dir=$HOME/.config/google-chrome/cloud9 http://127.0.0.1:3000 &
exit
```

Make it executable:

```
chmod +x ~/local/chrome-profilelauncher.sh
```

To delete the profile, in case you are uninstalling everything, simply remove the profile folder:

> **WARNING:** Be careful when using rm command with -r option. Make sure you type the path correctly, otherwise it might delete other stuff without prompting. To be safe, use the file manager instead.

```
rm -r ~/.config/google-chrome/cloud9
```


*4.3 Configuring a cloud9 browser profile in Opera*

Unfortunately, Cloud9 doesn't seem to work well with Opera.


**5. Customizing cloud9 profile**

*5.1 Theme*

*[Bloomind FT DeepDark 2]("https://addons.mozilla.org/en-US/firefox/addon/bloomind-ft-deepdark-2/")* theme for Firefox integrates wonderfully with Cloud9 IDE:

[IMG]https://static-cdn.addons.mozilla.net/img/uploads/previews/thumbs/60/60580.png?modified=1310746116[/IMG]


For Chrome, I suggest [Tiësto theme]("https://chrome.google.com/webstore/detail/mnmeobddjkkgkglnogihcaejaleikhdh?hl=en").

[IMG]https://lh5.googleusercontent.com/zMwFT0q0JsmOVfHiIC37EkPqVnmo2xX0voUiAJkB4E9I6xRIMNrlKNyPf3mGC0pBlA8QgycX4g=s128-h128-e365[/IMG]



*5.2 Customizing the interface *

You might want to hide some toolbars and icons in Firefox. Right-click on a toolbar, select *Customize*, then drag everything you don't need to the customization dialog and everything you need from the various toolbars and from the customization dialog, to the Tabs bar and click *Done*. Then right-click on a toolbar and untick *Add-ons Bar*, *Navigation Toolbar*, *Bookmarks Toolbar* and *Menu Bar*. Tick *Tabs on Top*.

For example, this is how my cloud9 profile toolbar looks like:

[[IMG]http://www5.picturepush.com/photo/a/6182588/640/6182588.png[/IMG]](http://picturepush.com/public/6182588)


*5.3 Hide the window border*

To hide the window border we can use the window rules feature of the window manager.

*5.3.1 Gnome Unity*

Unity maximizes applications by default and Firefox has global menu integration, so there is no title bar.

*5.3.2 KDE Kwin*

Right-click on the cloud9 profile window border, then select *Advanced >> Special Window Settings...*, then click *Window Extra* tab. In the Window title option paste:

**On Firefox:** *Cloud9 - Your code, anywhere anytime. - Mozilla Firefox* 

**On Chrome:** *Cloud9 - Your code, anywhere anytime. - Google Chrome*

Select *Exact Match* option. In the *Geometry* tab, tick *Maximized horizontally* and *Maximized vertically*, select *Remember* for both and tick the checkboxes. In the *Preferences* tab, tick *No border*, set to force and tick the checkbox. Click OK.



**6. Chromeless (experimental)**

Mozilla has killed Prism, which allowed to run web pages as standalone apps. However, Mozilla Labs folks are now working on the [Chromeless]("http://mozillalabs.com/chromeless/") project, which can provide a somewhat similar experience.

[Webian Shell]("http://mozillalabs.com/chromeless/2011/05/31/webian-shell-a-full-screen-web-browser-built-on-chromeless/"), which is based on Chromeless, can easily provide such experience. To install Webian Shell, simply [download]("http://webian.org/shell/download/") it, extract it to the ~/local folder or somewhere else and execute the binary inside the extracted folder.

Here is what Cloud9 looks like in Webian Shell:

[[IMG]http://www4.picturepush.com/photo/a/6182637/640/6182637.png[/IMG]](http://picturepush.com/public/6182637)

Enjoy!

---

### Post by itagomo on 2011-08-14
is this free? i mean all of it is free?

---

### Post by lovinglinux on 2011-08-15
> **itagomo said:**
> is this free? i mean all of it is free?

Yes.

---

### Post by itagomo on 2011-08-15
i was using the online version then a 'Trial Mode' appears in my dashboard. after few research, i found out there will be some kind of a extension.

cloud9ide.lighthouseapp.com/projects/67519/tickets/372-trial-mode-on-cloud9-ide

just curious if it's really free or not.

---

### Post by lovinglinux on 2011-08-15
> **itagomo said:**
> i was using the online version then a 'Trial Mode' appears in my dashboard. after few research, i found out there will be some kind of a extension.

cloud9ide.lighthouseapp.com/projects/67519/tickets/372-trial-mode-on-cloud9-ide

just curious if it's really free or not.

Yes, it is totally free if you install locally. They only charge for the online service, which also has a limited free plan.

---

### Post by itagomo on 2011-08-16
thanks for sharing this tutorial bro

---

### Post by lovinglinux on 2011-08-16
> **itagomo said:**
> thanks for sharing this tutorial bro

You are welcome.

---

### Post by neuromancer2701 on 2011-12-01
I have installed and got Cloud9 running on a gumstix.  I have setup a reverse proxy to get to the localhost:3000 port.  

It seems to be working but the cloud9 site keeps giving me a browser incompatible page.  I have tried the latest versions of Firefox and Chrome.  Anything i can do to disable the browser check?  

Thanks

---

### Post by lovinglinux on 2011-12-01
> **neuromancer2701 said:**
> I have installed and got Cloud9 running on a gumstix.  I have setup a reverse proxy to get to the localhost:3000 port.  

It seems to be working but the cloud9 site keeps giving me a browser incompatible page.  I have tried the latest versions of Firefox and Chrome.  Anything i can do to disable the browser check?  

Thanks

Try [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59/).

---

### Post by neuromancer2701 on 2011-12-05
Is there a setting in Cloud9 that will load the IDE no matter what the browser version is?

---

### Post by lovinglinux on 2011-12-05
> **neuromancer2701 said:**
> Is there a setting in Cloud9 that will load the IDE no matter what the browser version is?

Not that I am aware of.

---

### Post by jmate24 on 2011-12-07
in installing o3 i am having trouble when it comes to:

justin@justin-nemumacme:~/cloud9ide/o3$ ./tools/node_modules_build
The "sys" module is now called "util". It should have a similar interface.
Checking for program g++ or c++          : /usr/bin/g++ 
Checking for program cpp                 : /usr/bin/cpp 
Checking for program ar                  : /usr/bin/ar 
Checking for program ranlib              : /usr/bin/ranlib 
Checking for g++                         : ok  
Checking for node path                   : [COLOR="Orange"]not found[/COLOR] 
Checking for node prefix                 : ok /home/justin/cloud9ide

23:24:59 runner system command -> ['/usr/bin/g++', '-g', '-O3', '-msse2', '-ffast-math', '-fPIC', '-DPIC', '-D_LARGEFILE_SOURCE', '-D_FILE_OFFSET_BITS=64', '-D_GNU_SOURCE', '-IRelease/include', '-I../include', '-IRelease/hosts', '-I../hosts', '-IRelease/modules', '-I../modules', '-IRelease/deps', '-I../deps', '-I/home/justin/cloud9ide/include/node', '../hosts/node-o3/sh_node_libs.cc', '-c', '-o', 'Release/hosts/node-o3/sh_node_libs_1.o']
../include/cSys_posix.h: In member function &#8216;virtual void o3::cMessageLoop::post(const o3::Delegate&, o3::iUnk*)&#8217;:
../include/cSys_posix.h:414:43: warning: ignoring return value of &#8216;ssize_t write(int, const void*, size_t)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
[3/3] [COLOR="orange"]cxx_link: build/Release/hosts/node-o3/sh_node_1.o build/Release/hosts/node-o3/sh_node_libs_1.o -> build/Release/o3.node[/COLOR]

there is no build/Release/o3.node?

is there a way to fix it? i am really interested in learning to program so i can make my own media player that will hopefully fix the major issues i have been having with banshee, rhythmbox and songbird.

---

### Post by lovinglinux on 2011-12-07
I haven't tested this on Oneiric.

---

### Post by Kamal Reddy on 2012-03-17
when I tried this command: bin/cloud9.sh
I got an error saying

support/node-builds-v4/node-linux32: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory


It would be kind of you if you can help me out here.
Thanks

---

### Post by eruducer on 2012-03-18
Hi! thx for the tutorial! There is just one little problem: When I run the ```
~/local/node ~/local/cloud9/bin/cloud9.js -w ~/pathtoyourproject
``` I get the error: ```
bash: ~/local/node: Is a directory
```.
Does anyone know how to fix it?

---

### Post by Wexlatron on 2012-03-18
> **eruducer said:**
> Hi! thx for the tutorial! There is just one little problem: When I run the ```
~/local/node ~/local/cloud9/bin/cloud9.js -w ~/pathtoyourproject
``` I get the error: ```
bash: ~/local/node: Is a directory
```.
Does anyone know how to fix it?

Try this:
```
~/local/node/**node** ~/local/cloud9/bin/cloud9.js -w ~/pathtoyourproject
```
It worked for me. My guess is the OP must have left this out by mistake.

---

### Post by Wexlatron on 2012-03-20
Okay this guide is kind of old now. These directions will only get you version 0.5 because they no longer use the devel branch anymore. This sucks because latest release has nice features like autocompete. So anyway this is how I did it (I think).

I'm not sure if all these packages are necessary or not but just to make sure I'll include this.
```
sudo apt-get install -y build-essential g++ curl libssl-dev apache2-utils git libxml2-dev
```
You'll want to install nodejs, nodejs-dev and npm from the repositories. I used Synaptic but I guess doing the following command might work. (I'm not certain but it's possible just doing the below command will pull in all of the dependencies you'll need.)
```
sudo apt-get install -y nodejs nodejs-dev npm
```

And last I just installed Cloud9 by doing
```
git clone git://github.com/ajaxorg/cloud9.git
cd cloud9/
bin/cloud9.sh
```

Bingo something like the following should pop up in your running browser.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214666&d=1332283350[/IMG]

Edit:
[B]To Launch cloud9 using your project path do:
[/B]```
~/cloud9/support/node-builds-v4/**node-linux32**  ~/cloud9/bin/cloud9.js -w ~/*pathtoyourproject*
```
**(I don't have a 64bit system)**

---

### Post by nailliK on 2012-04-23
Everything seems to work OK until I actually type in my.ip.address:3000 into my browser. 
I've tried adding port 3000 to iptables but it doesn't seem to help.
Does this only work locally?

---

### Post by lovinglinux on 2012-04-23
> **nailliK said:**
> Everything seems to work OK until I actually type in my.ip.address:3000 into my browser. 
I've tried adding port 3000 to iptables but it doesn't seem to help.
Does this only work locally?

I haven't tried this in a long time. The tutorial is now considered outdated and was moved to the corresponding forum.

---

### Post by nailliK on 2012-04-23
> **lovinglinux said:**
> I haven't tried this in a long time. The tutorial is now considered outdated and was moved to the corresponding forum.

Thanks for the reply. Could you kindly send a link to the correct forum thread?

---

### Post by lovinglinux on 2012-04-23
> **nailliK said:**
> Thanks for the reply. Could you kindly send a link to the correct forum thread?

What do you mean? The thread is this one, but the tutorial is old and should be ignored.

---

