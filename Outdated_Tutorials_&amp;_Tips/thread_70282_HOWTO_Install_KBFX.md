---
title: "HOWTO: Install KBFX"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-09-29
This guide is aimed at newbies (as it's easy to follow) and at everyone who want to make his/her desktop a bit more eyecandy (it will substitute your start menu). You can customise the button according to your taste.
It works in KDE ONLY (but it doesn't damage GNOME in any way, you just can't use it in GNOME)

You can have a look at a screenshot of my former desktop computer sporting a Kubuntu button:

[http://ubuntuforums.org/gallery/showimage.php?i=700&original=1&c=3]("http://ubuntuforums.org/gallery/showimage.php?i=700&original=1&c=3")

[COLOR="Red"]UPDATE: Now you can see the package in Synaptic/Kynaptic and uninstall it as any other application. Moreover a .deb will be generated and you will not have to repeat the compilation from source any more (you will use the .deb package)[/COLOR]


1) Open Synaptic/Kynaptic

Press the &#8220;Search&#8221; button

Type &#8220;kdevelop&#8221; in the search field and press enter

You will see a list of files

select &#8220;kdevelop&#8221; and &#8220;kdevelop3-dev&#8221; (click on the empty square beside these names and select &#8220;Mark for Installation&#8221;)

Press the &#8220;Search&#8221; button again

Type &#8220;build&#8221; in the search field and press enter

select &#8220;build-essential&#8221; (click on the empty square beside these names and select &#8220;Mark for Installation&#8221;)

Press the &#8220;Search&#8221; button again

Type &#8220;checkinstall&#8221; in the search field and press enter

select &#8220;checkinstall&#8221; (click on the empty square beside these names and select &#8220;Mark for Installation&#8221;)

Press the &#8220;Apply&#8221; button (then it will ask you for confirm, click Apply again)

Close Synaptic/Kynaptic

2) Download Kbfx source from the link below

[http://www.kde-look.org/content/show.php?content=24898]("http://www.kde-look.org/content/show.php?content=24898")

(get the latest release)

3) Open Terminal/Konsole and type:

cd  the_folder_in_which_you_put_the_file_you_downloaded

e.g. cd OperaDownloads  in my case 

tar -xjf kbfx-4.7.3.tar.bz2 (the name of the file you downloaded, which may vary from mine)

cd kbfx-4.7.3 (according to the name of the folder created by your file)

./configure --prefix=/usr (DON'T forget the dot &#8220;.&#8221; at the beginning of the line)
sudo make

sudo checkinstall

At a certain point it will ask you some question: press ENTER to use the default answer

Then the following sentence will appear:
[QUOTE=]Please write a description for the package.
End your description with an empty line or EOF.
>> [/QUOTE]

You can write a description if the package if you wish (otherwise leave it blank and press ENTER two times) [COLOR="Blue"](e.g. I put "Suse win deco" because I was not installing kbfx but the process is the same but the name of YOUR package will be kbfx)[/COLOR]
Press ENTER two times

Then it will ask you (this is just an example): 
[QUOTE=]This package will be built according to these values:

0 -  Maintainer: [ [email]root@localhost.loca[/email]ldomain ]
1 -  Summary: [ Suse win deco ]
2 -  Name:    [ kwin-decor-suse2-0.3 ]
3 -  Version: [ 0.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kwin-decor-suse2-0.3 ]
9 -  Alternate source location: [  ]

Enter a number to change any of them or press ENTER to continue:[/QUOTE]

Press ENTER (unless you want to modify something)

Now you have made a .deb package of the desired program (next time you can use this to install it) (inside the folder containing the source) and you will see the program in synaptic/kynaptic too (this means you can uninstall it as any other application)

3) Ok, now you have installed the latest version of KBFX.

Now let's make it work

Right click on the panel (the main panel where you have the start menu and other icons) and select /Add to panel/Applet/kbfx

A new button will appear.

If you want to customise the button you have to download a kbfx button from [http://www.kde-look.org/]("http://www.kde-look.org/") (type kbfx in the search engine of the website)

You can drag and drop the image of the button you wish to use into the current kbfx button.

4) The size of the image usually doesn't match the size of the button, try this:

Right click on the panel (NOT ON KBFX BUTTON!) (do it on a free space)

and select /Remove from panel/Applet/kbfx

then again Right click on the panel and select /Add to panel/Applet/kbfx

Now it will match the size of the image.

5) If the result pleases you you can remove your kmenu button (you can always put it back if you wish)

Right click on the &#8220;kmenu&#8221; (the start menu) and select &#8220;Remove k menu&#8221;

6) Click on the left handler of  your kbfx button in order to move it and place it at the extreme left side of the panel (where your start menu was)

NOTE: If the kbfx button doesn't match the size (width) of the panel you will have to modify the size of your panel (quite obviously)

Enjoy your new button!

Alberto

---

### Post by Jonathan2007 on 2005-10-08
Thanks a lot for this guide.

But I ran into one problem. You said you need to do a ```
./configure –prefix=/usr
``` but that doesn't work. You need to do a ```
./configure --prefix=/usr
```. Please change that in your post.

Other than that it worked great. I had previously had the deb version of kbfx (the one that is floating around here on the forums). I couldn't figure out how to uninstall it so I just compilled and hopefully installed this one over the other one. The other one was an old version too so that is why I am upgrading.

Thanks again for the guide. :)

---

### Post by tseliot on 2005-10-08
[QUOTE=Jonathan2007]Thanks a lot for this guide.

But I ran into one problem. You said you need to do a ```
./configure &#8211;prefix=/usr
``` but that doesn't work. You need to do a ```
./configure --prefix=/usr
```. Please change that in your post.

Other than that it worked great. I had previously had the deb version of kbfx (the one that is floating around here on the forums). I couldn't figure out how to uninstall it so I just compilled and hopefully installed this one over the other one. The other one was an old version too so that is why I am upgrading.

Thanks again for the guide. :)[/QUOTE]
You're right. It was a typo but I've fixed it now. Thanks for making me notice it

---

### Post by farmer on 2005-10-11
You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.

---

### Post by tseliot on 2005-10-12
[QUOTE=farmer]You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.[/QUOTE]
Very interesting, thanks :)

---

### Post by tseliot on 2005-10-16
[QUOTE=farmer]You should also look into using .debs instead of make install.[Checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/index.php") is the tool that does it.  The backports people can tell you more about that works. I only know it's there.[/QUOTE]
Guide updated!

---

