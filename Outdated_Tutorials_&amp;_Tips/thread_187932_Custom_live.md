---
title: "Custom live"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by vignesh on 2006-06-03
HI!
  
I am making the next version of my Hoary based livecd using the image of my previous version.I have the following questions.

1.How to add vlc player to the Multimedia menu
2.To disable the autologin of user ubuntu in the gettys.. I know I have to remove the user ubuntu but I don`t wanna mess up.
3.No autologin.What file do I have to edit ?
4.New GDM
5.New default theme
6.Can I change the default user name...I know I have to change the name in the sudoers list as well... Will that bring up any problems.
7.I am modifying a Mac OS X default wallpaper and using it as my default... Is that illegal or somethin.. (Just curious)
8.Also no sound comes in Frozen-Bubble,supertux and tuxracer .. It worked on my installed system.I used the same packages to alter the livecd as well

  Blender and a SudoKu game both are not packages.. binary files... So also have to add them to the menu.
9.I am going to install wine also..How do preconfigure it.
10.Auto mounting hardisk partitons... I want to write my own script.. Any suggestions

/proc/partitions contains all the partitons... right ? How to proceed after that.

11.I also going to install window maker what are config files for that.. tochange wallpaper.

Cheers!

---

### Post by tkjacobsen on 2006-06-03
It will probably be easyist to build a custom livecd using the tools provided by DSS:
[http://www.dsslive.org/](http://www.dsslive.org/)

I know it is not ubuntu-based, but it is made to make live cds though - and it is still based on debian

7) Yes this will probably be illegal since OS X is proprietary..


EDIT: Directly from the FAQ
What is dsslive ?

It's a pure, default debian|ubuntu system booting up from a cdrom, providing a framework for livecd creation. 

So it is still a little ubuntu... If you would like to see a live example check out elive: elivecd.org . Version 0.5  (currently under development) us made from DSS

EDIT2: they even have a tutorial: [http://www.dsslive.org/mediawiki/index.php/How_To:_Lazy_Mode](http://www.dsslive.org/mediawiki/index.php/How_To:_Lazy_Mode)

---

### Post by vignesh on 2006-06-04
But still I can use the pic as a wallpaper right... Its only for personal use not like I am going to sell it or somethin..

I want to do it on my own.. I dropped two things 

wine and Automount 

Just tell me how to make desktop icons or edit the menu that should do ... Anyone know how to do that ?

---

### Post by tkjacobsen on 2006-06-08
i found this howto, maybe you can use some of that

---

