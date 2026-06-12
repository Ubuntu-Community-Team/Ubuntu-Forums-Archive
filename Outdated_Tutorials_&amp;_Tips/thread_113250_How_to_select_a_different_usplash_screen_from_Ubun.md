---
title: "How to select a different usplash screen from Ubuntu to Kubuntu to Xubuntu"
date: 2006-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by byen on 2006-01-06
Hey Guys,
Today when I installed a new kernel I was suprised to see that after the installation completed ..my default ubuntu splash screen changed to kubuntu. I tried looking around and realized that there were many users facing the same issue either after a new kernel install or after installing kde over ubuntu (the splash screen somehow changed to Kubuntu or Xubuntu (incase of an XFCE install)). So after digging around I found out that there is an easy way.

(Please note that this how-to has been tested and seems to work on Breezy as well as Dapper)

Here is what you do:

Open the terminal and type:

> [COLOR="Blue"]sudo update-alternatives --config usplash-artwork.so[/COLOR]

(this will open a selection box that lets you decide which splash you would prefer 1.default(ubuntu) 2.kubuntu and 3.xubuntu. select one and then press <enter>)
Now enter:

> [COLOR="#0000ff"]sudo dpkg-reconfigure linux-image-`uname -r`[/COLOR]
Note that the quotes for uname-r are not the "forward" ones under the double quote (") key, they are "back" quotes (usually found with the ~) key.
(this will build your choice into the initramfs) (enter)

You can also alternately use this instead of the above command
>  sudo dpkg-reconfigure linux-image-$(uname -r)

It will take about 10-30 seconds and thats it! you are done!!
Restart and enjoy!
It worked for me..so I think it might just work for you.
Goodluck.
(Thankyou groggyboy and mbeierl for the additional info that has now been added to this howto)

# For more info about customized usplash.[.click here]("https://wiki.ubuntu.com/USplashCustomizationHowto") (Wiki)
# If you are looking for customized usplash themes with different colors. [click here]("http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash")
# If you wish to change the uspash time out . [Click here]("http://ubuntuforums.org/showthread.php?t=76309")
# To customize you Ubuntu Grub, Usplash and system colors to blue / other themes etc.[click here ]("http://ubuntuforums.org/showthread.php?t=83009&highlight=usplash")

---

### Post by montes.c on 2006-01-19
update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.


But I still get kubuntu ?

---

### Post by byen on 2006-01-19
what happens when you do
sudo apt-get -f install usplash

---

### Post by montes.c on 2006-01-19
xochiyotl# apt-get -f install usplash
Reading package lists... Done
Building dependency tree... Done
usplash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by byen on 2006-01-19
I think the ubuntu usplash somehow got deleted or overwritten..why dont you [try this]("http://ubuntuforums.org/showthread.php?t=82835&highlight=usplash")...  it just manually replaces the splash image with the one you select.
Sorry its not a more direct answer but see if that link helps...

---

### Post by montes.c on 2006-01-20
I skipped the first command you recommended and just did this one:

sudo dpkg-reconfigure linux-image-`uname -r`

It worked.....thanks :)

---

### Post by byen on 2006-01-20
lol...well.. COOL!

---

### Post by dunnerz on 2006-02-16
Brilliant - this helped me too

Thanks.

---

### Post by MerZo on 2006-03-13
Thanks, was looking for a solution!

---

### Post by sportsfan986 on 2006-03-13
Can you get rid of the status bar and the text showing what has been loaded on the splash screen durring startup?

---

### Post by byen on 2006-04-29
sportsfan986. I am not sure if getting rid of the status bar is simple. If I find out more abt it.. I will update my howto accordingly.
~byen

Edit: Nope.. looks like trying to get rid of the status bar ends up crashing the usplash. Im not sure if it is even worth trying. Sorry Sportsfan986.. If anyone knows more abt the statusbar options please let us know.Thanks!

---

### Post by groggyboy on 2006-05-13
I cant get this command to work:> sudo dpkg-reconfigure linux-image-'uname -r'

Use this instead:> sudo dpkg-reconfigure linux-image-$(uname -r)

-cheers, groggyboy

---

### Post by byen on 2006-05-14
Hey Groggyboy,
I have tried and tested this on Breezy and to the best of my knowledge this seems to work. From your Nick Info I see that you are currently using Dapper? so was this issue on your Dapper install? and did the command you mentioned work on Dapper? Please let me know so that I can update my howto accordingly. Thanks for the heads up :P
~byen

---

### Post by CrashOverKill on 2006-05-14
I tried to build my own Splash and well.........I get a black screen LOL but it boots finally. Not sure where I went wrong. Here is the splash I made.

---

### Post by xtacocorex on 2006-05-15
I think usplash themes can only have, if I remember off the top of my head correctly, 16 colors like grub themes. 

Here is a link to the wiki on usplash customization.
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

---

### Post by Mr Fat Bat on 2006-05-16
Wow that was the fastest solution out of all those little things that go wrong I've ever seen ;) Much thanks!

---

### Post by groggyboy on 2006-05-16
Byen: I am running dapper.  Before I go claiming that the command I had to use is the command everyone has to use in dapper, you should maybe get some other dapper user to test it out.  It might very well be due to some package or other I have installed.

Nonetheless, using "linux-image-'uname -r' simply doesn't work for me.

But whatever the case, the end result is the same.

Thanks for the how to!

groggyboy

---

### Post by mbeierl on 2006-05-16
Don't forget that the quote characters in the command

linux-image-`uname -r` 

are not the "forward" ones under the double quote (") key, they are "back" quotes (usually found with the ~) key.

Using backquotes causes the command inside to be executed and the output used in place.

eg:

$ uname -r
2.6.16

$ echo linux-image-'uname -r'
linux-image-uname -r

$ echo linux-image-`uname -r`
linux-image-2.6.16

---

### Post by groggyboy on 2006-05-21
mbeierl - that would explain why it wasn't working for me.

in any case, both "linux-image-`uname -r`" and "linux-image-$(uname -r)" work.

---

### Post by byen on 2006-05-22
I have now tested this How-to on Breezy as well as on Dapper and it seems to work well. groggyboy and mbeierl, thank you for your input! I have now updated my how-to based on the information you guys have provided here. Thank you guys!
~byen

---

