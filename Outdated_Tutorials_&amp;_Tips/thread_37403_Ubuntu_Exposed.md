---
title: "Ubuntu Exposed"
date: 2005-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by grexk on 2005-05-27
This is my first time to post in this section...hope you will learn from me and help me also to learn....

FIRST HOWTO
1. UBUNTU Splash Howto:
 First open gconf editor, then after opening it edit
 * /apps/gnome-sessions/options/splash_image
 change the value splash/ubuntu-splash.png with your splash and place your splash image to
 /usr/share/pixmaps/splash directory.
 [Old]
 /apps/gnome-sessions/options/splash_image=splash/ubuntu-splash.png
 
 [New]
 /apps/gnome-sessions/options/splash_image=splash/gnome-splash.png

 You can also change the background color of the splash by editing your 
 /etc/gdm/gdm.conf file. Find "BackgroundColor" change the default value
 #523921(HUMAN) to ur color.

 NOTE: The are Debian splash and backgrounds are located in /usr/share/images/desktop-base.
  
2. Changing UBUNTU tty login message(aka issue):
 
 [Old]
 Ubuntu 5.04 .....
 Login:

 you should edit /etc/issue, change it to your likes.
 
 [New]
 Ubuntu 5.04 ..../etc/issue modified by grexk
 Login:

3. Change UBUNTU Motd file ("can you give me the meaning of MOTD....hehe"):
  
  [Old]
  "Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
  The programs included with the Ubuntu system are free software;
  the exact distribution terms for each program are described in the
  individual files in /usr/share/doc/*/copyright.

  Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
  applicable law."
   
  This will message appear after loging to tty. You can edit the file located
  in /etc/motd file with your messages after user login.
  
  [New]
  "Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux 
   Welcome to the world of linux, forget Windows.-/etc/motd modified by grexk

4. ROOT "rm *" command:
  The default installation Ubuntu does'nt  alias the command "rm" to "alias rm='rm -i'"
  so be sure to edit ur ~/.bashrc file in you /home/u or /root directory before doing a mistake 
  with rm command. Uncomment the following lines to ur .bashrc
  
  [Old]
  43 # Some more alias to avoid making mistakes:
  44 #alias rm='rm -i'
  45 #alias cp='cp -i'
  46 #alias mv='mv -i' 
  
  [New]
  Some more alias to avoid making mistakes-modified by grexk
  alias rm='rm -i'
  alias cp='cp -i'
  alias mv='mv -i'

5.Changing ur panel behavior:
  First open gconf editor, then after opening it edit
  * /apps/panel/toplevels/bottom_panel_screen0/auto_hide 
    - this key will auto hide your panel,togel the checkbox to enable it.
  * /apps/panel/toplevels/bottom_panel_screen0/unhide_delay
    - this key will unhide your panel in milliseconds. The default value is 500 which 
    is very slow I suggest the you change the value to 20 for faster appearance.
  * /apps/panel/toplevels/bottom_panel_screen0/hide_delay
    - this key will hide your panel in milliseconds. The default value is 500 which is just
    enough but you can change it to 20 for faster hiding.
  * /apps/panel/toplevels/bottom_panel_screen0/enable_buttons
    - this key will enable/hide buttons at the left and right of the panel,
    togel the checkbox to enable it.
  * /apps/panel/toplevels/bottom_panel_screen0/enable_arrows
    - this key will enable/hide the arrow keys of the left and right of the panel,
    togel the checkbox to enable it.
    Note: Output will not be notice if you does'nt enable ".../enable_buttons" key.
 
  The other keys are simple so just try experimenting with the 
  values and read the short description. If you want to reset the values
  to default just unset the key (right-click to the value)
6. Splashing your grub:
  * This howto based from the work of Luis R. Rodriguez <mcgrof@ruslug.rutgers.edu>
  First prepare an image.
    * xpm.gz file type
    * 640x480
    * 14 colors only
  You can find some of GRUB splash on the net by googling.If you want to create/convert 
  images of a different type (jpg,png,*) you can use gimp. In gimps menu goto 
  "Image-->Mode-->Indexed" be sure to specify the maximum colors to 14. 
  If you did'nt specify the maximum colors to 14 ur splash image wont work.
  Then after that save ur image to xpm format(image.xpm). You may be asking why should
  I gunzip my image "image.xpm.gz", to make it load faster but you can also 
  leave it alone as "image.xpm". Now you are ready with your splash image, place the file
  in your "/boot/grub/image.xpm.gz" or  create "image" folder 
   "/boot/grub/image/image.xpm.gz" to manage your GRUB splash easier.
  
  TODO:
  1. Add this "splashimage" to your menu.lst.
  
  splashimage=(hd0,0)/boot/grub/image.xpm or splashimage=(hd0,0)/boot/grub/image.xpm.gz
  
  *(hd0,0)-This means that from now on, GRUB will parse / as (hd0,0)/
  * /boot/grub/image.xpm -location of your GRUB splash image.
  
  In UBUNTU default menu.lst comment the ff. lines and place "splashimage":
  
  ........
  ## hiddenmenu
  # Hides the menu by default (press ESC to see the menu)
  #hiddenmenu <-- COMMENT ME

  # Pretty colours
  #color cyan/blue white/blue <-- COMMENT ME
  
  #Splash Image for GRUB
  splashimage=(hd0,0)/boot/grub/debian2.xpm
  ........

  This should also work:
  ........
  ## hiddenmenu
  # Hides the menu by default (press ESC to see the menu)
  #hiddenmenu

  # Pretty colours
  #color cyan/blue white/blue
  
  ## default grub root device
  ## e.g. groot=(hd0,0)
  groot=(hd0,0) #<-- UNCOMMENT ME
  
  #Splash Image for GRUB
  splashimage /boot/grub/debian2.xpm   
  .................
  
  
  Now be ready to blow up your system..."Actually I rebooted 8 times just to work this
  out". You should reboot by now to see the outcome. If see blank screen w8 for defualt time
  entry. Then try checking your image or menu.lst.


  Changelog:
  added grub splash howto- 5/29/05 
  updated my HOWTO - 5/27/05

---

