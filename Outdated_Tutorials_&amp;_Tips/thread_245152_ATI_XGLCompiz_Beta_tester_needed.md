---
title: "ATI XGL/Compiz Beta tester needed"
date: 2006-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by chokes on 2006-08-27
**[SIZE=4]First section[/SIZE]**
First make sure you have 3d acceleration available in a normal Gnome session. There are lots of howtos for this , Google if you need any help with that. So if glxinfo shows direct rendering: yes , then you are good to go. If not XGL and Compiz wont work!

**If you own an X series Radeon card , scroll down to the end of this HowTo!**

This First metod is starting Xgl in root not over X....[LIST]
[*]Update your system:[/LIST]```
  sudo aptitude update && sudo aptitude dist-upgrade  
```[LIST]
[*]Prepare and update repositories:[/LIST]```
sudo gedit /etc/apt/sources.list
```[LIST]
[*]Add quinstorms' and reggaemanus'     repositories to /etc/apt/sources.list:[/LIST]```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
```[LIST]
[*]Download and import the gpg key     for quinnstorms repository:[/LIST]```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add - 
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add - 
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
```[LIST]
[*]update your sources:[/LIST]```
  sudo aptitude update
```[LIST]
[*]Install needed packages:[/LIST]```
  sudo aptitude install xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes
```[LIST]
[*]Modify /etc/gdm/gdm.conf-custom:[/LIST]```
  sudo gedit /etc/gdm/gdm.conf-custom
```[LIST]
[*]Look for [servers] and paste     this:[/LIST][```
servers] # Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl 

[server-Xgl]  name=Xgl server  command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true
```[LIST]
[*]Modify /etc/gdm/gdm.conf :[/LIST]```
  sudo gedit /etc/gdm/gdm.conf
```[LIST]
[*]And change:[/LIST]```
  0=Standard 
#1=Standard 
``` 
to

```
  #0=Standard 
1=Standard
```[LIST]
[*]Go to line 198 and change     GdmXserverTimeout=10 to (this one is very crucial):[/LIST]```
 GdmXserverTimeout=50  
```[LIST]
[*]Do another dist-upgrade so you are sure you have all the     newest packages:[/LIST]```
  sudo aptitude update && sudo aptitude dist-upgrade
```[LIST]
[*]Reboot , Login and have fun![/LIST]To start compiz you have to right click on the red icin in notification aera and clik on : GL Desktop
 

 


 [B][SIZE=4]Second Section[/SIZE]
First make sure you have 3d acceleration available in a normal Gnome session. There are lots of howtos for this , Google if you need any help with that. So if glxinfo shows direct rendering: yes, then you are good to go. If not XGL and Compiz wont work!

Tih method is starting Xgl in cover of X its more stable but use more memory. And you will not be able to shut down or restart the computer.

[/B]Update your system:```
  sudo aptitude update && sudo aptitude dist-upgrade
```[LIST]
[*]Prepare and update repositories:[/LIST]```
  sudo gedit /etc/apt/sources.list
``` 
Add quinstorms repositories
```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx 
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
```[LIST]
[*]Download and import the gpg key     for quinnstorms repository:[/LIST]```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add - 
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add - 
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
```[LIST]
[*]update your sources:[/LIST]```
  sudo aptitude update
```[LIST]
[*]Install needed packages:[/LIST]```
  sudo aptitude install xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes
```[LIST]
[*]Make a startup script for XGL:[/LIST]```
sudo gedit /usr/bin/startxgl.sh
```[LIST]
[*]Paste:[/LIST]```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME 
exec gnome-session
```[LIST]
[*]Make the script executable:[/LIST]```
  sudo chmod 755 /usr/bin/startxgl.sh
```[LIST]
[*]Make a XGL session for the login     manager:[/LIST]```
  sudo gedit /usr/share/xsessions/xgl.desktop
```[LIST]
[*]Paste:[/LIST]```
[Desktop Entry] 
Encoding=UTF-8 
Name=XGl 
Exec=/usr/bin/startxgl.sh 
Icon= 
Type=Application
```[LIST]
[*]Do another dist-upgrade so you are sure you have all the     newest packages:[/LIST]```
  sudo aptitude update && sudo aptitude dist-upgrade
```[LIST]
[*]reboot.[/LIST]In the login manager you can now choose a session named Xgl. Answer to following question that you want to use XGL for this session only (if something went wrong you are logged in next time using standard session) If everything works fine , you can set it as the default session , remember you can always login a normal gnome session if you want.


 To start compiz you have to right click on the red icon in notification aera and clik on : GL Desktop
 
**[SIZE=4]Additional Notes:[/SIZE]**
If you own an X series Radeon and have problems with lockups, do this:
```
  sudo gedit /etc/X11/xorg.conf
``` 
Find the Driver section for your video card and add this as the option:
```
  Option       "KernelModuleParm" "agplock=0"
``` 
Note for all cards: glxinfo will show that direct rendering is not working , don't worry that's normal when you are running XGL.

** Please Let me know if someting wrong with this How to and tell me what do you think** ;)

Here A link to the wiki page for configuring Compiz in Gconf-editor:smile:
[https://help.ubuntu.com/community/Co...ngCompiz#xprop]("https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz#xprop")
[B]
[SIZE=5]Removal for the first method -[/SIZE][/B]

----------------------

Prepare and update repositories:
     [LEFT]```
sudo gedit /etc/apt/sources.list
```[/LEFT]
      
 
Remove or comment out (#) quinstorms' and reggaemanus' repositories to /etc/apt/sources.list:
     [LEFT]```
#deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx 
#deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx 
#deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
```[/LEFT]
      
 
Remove instaled packages:
     
```
[LEFT]sudo aptitude remove xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes[/LEFT]
      
```  
Modify /etc/gdm/gdm.conf-custom:
     [LEFT]```
  sudo gedit /etc/gdm/gdm.conf-custom
```[/LEFT]
      
 
Look for [servers] section and delete this:
        
```
[LEFT] 1=Xgl 

[server-Xgl]  name=Xgl server  command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true[/LEFT]
      
```  
Modify /etc/gdm/gdm.conf :
     
```
[LEFT]  sudo gedit /etc/gdm/gdm.conf[/LEFT]
      
```  
    * And change:

     [LEFT]```
#0=Standard 
1=Standard
```[/LEFT]
      
 
to
     [LEFT]```
0=Standard 
#1=Standard
```[/LEFT]
        
reboot

[SIZE=5]**Second section removal:**[/SIZE]

update repositories:

[LEFT]```
  sudo gedit /etc/apt/sources.list
```[/LEFT]
    
 
Comment (#) out the following or delete:

 [LEFT]```
#deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx 
#deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx 
#deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx
```[/LEFT]
     remove packages  

```
[LEFT] sudo aptitude remove xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes[/LEFT]
    
``` Remove start up script and XGL session for login manager

Delete: 

[LEFT]```
sudo rm /usr/bin/startxgl.sh
sudo rm /usr/share/xsessions/xgl.desktop
```[/LEFT]
    
 
reboot

---

### Post by kosmic on 2006-08-28
I've tried the 2º section and it works.

My card is an ATI RADEON 9600 PRO.

---

### Post by chokes on 2006-08-28
you can start and stop compiz with the Compiz icon?

---

### Post by alexandermimix on 2006-08-28
before I try this, whats the likely hood it is going to work on a 64 bit system ?

Im really looking forward to getting this eye candy cranking!

---

### Post by The Soundophiliac on 2006-08-28
No. 2 works for me and I can start/stop compiz using the Compiz icon in the notification area.

I've been using the compiz-start.py script to start and manage compiz. Just tried gnome-compiz-manager. It's alright and I realize that gnome-compiz-preferences are newbie-friendlier but I do prefer gset-compiz for editing the preferences. It has features like choosing the cube top and bottom images and more comprehensive shortcut editing capabilities, for example. I guess I could use gconf-editor for that.

 Also, compiz-start.py has the option to restart compiz and to switch to metacity, which I like. Also IMHO it's good that in compiz-start.py you can go directly to the cgwd themer.

---

### Post by tribaal on 2006-08-28
I installed both ways, both work for me.

Good job :)

- trib'

---

### Post by S1NGH on 2006-08-28
alexandermimix: you will need amd64 packages, you can see this guide: [http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427)
me and chokes will update the guide, we will have both nVidia and ATi setup, since we are getting good feedback, we will post the guide with chokes nVidia guide and my ATi one, which is this.
chokes helped me with a few modifications. 

So far all seems well, are you guys experiencing slow downs or any problems or its all good?

---

### Post by tribaal on 2006-08-28
It's all good so far.
I'd say it's even faster than the other tutorials (beerorkid's repos seem to be more up-to-date).

I still have some XGL related questions, but it has nothing to do with the installation method, so I'll post them somewhere else :)

Cheers :)

- trib'

---

### Post by S1NGH on 2006-08-28
Thanks a lot tribaal and everyone else for the great feedback! :) appreciated your time and effort ;)

---

### Post by kosmic on 2006-08-28
> **chokes said:**
> you can start and stop compiz with the Compiz icon?

Yes I can :) no problems there

---

### Post by Sam on 2006-08-28
You should write something about the compiz configuration (or link the [wiki page](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz)).

---

### Post by chokes on 2006-08-28
> **S1NGH said:**
> alexandermimix: you will need amd64 packages, you can see this guide: [http://www.ubuntuforums.org/showthread.php?t=133427](http://www.ubuntuforums.org/showthread.php?t=133427)
me and chokes will update the guide, we will have both nVidia and ATi setup, since we are getting good feedback, we will post the guide with chokes nVidia guide and my ATi one, which is this.
chokes helped me with a few modifications. 

So far all seems well, are you guys experiencing slow downs or any problems or its all good?

I tried this how to and it too old and not working :(  ill retry to get this work when i reinstall ubuntu in AMD64

---

### Post by chokes on 2006-08-28
> **Sam said:**
> You should write something about the compiz configuration (or link the [wiki page]("https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz")).
Tanx sam :) we'll add this when we'll make the final Howto:)

---

### Post by alexandermimix on 2006-08-28
AMD64 3800+ dual core
and
ATI x800GT

---

### Post by hype on 2006-08-28
Just to give a little feedback, i used the second method some times ago now.
 But recently i noticed some really heavy Xgl CPU loads.
By exemple, watchin a video (using Vlc or Mplayer) was really smooth on quite older version of Xgl/compiz.
 Now, its quite choppy, and its nearly impossible to watch a movie in full screen. (Xgl uses something like 90/100% of the CPU)
 Another exemple, using unfold shortcut (ctrl+alt+PgDwn) i used to see the movie still running just smoothly ; now, it just stop for a few seconds a starts again, lets say...really choppy : unusable when watching a movie.

 I use latest compiz packages (using "main" repos), ATI 9600XT (Dirvers 8.28.8 ) Athlon Xp 1800+ 1Go ddr

---

### Post by chokes on 2006-08-28
you can try compiz-vanilla it will work smooth on your hardware or maybe your opengl isnt in direct riendering


oh and if you are using the water effect.... its take a lot of CPU so try disable some plugins...... the trailfocus plugin should be hard for your hardware

---

### Post by hype on 2006-08-28
> **chokes said:**
> you can try compiz-vanilla it will work smooth on your hardware or maybe your opengl isnt in direct riendering

Indeed, 
```
glxinfo | grep direct
direct rendering: No
```

But is it linked to the fact that, as sais in the how-to 
"Note for all cards: glxinfo will show that direct rendering is not working , don't worry that's normal when you are running XGL."

And actually most of plugins are working, were without 3D acceleration i just get a uber-slow crappy desktop; which is not (yet) the case here.

---

### Post by chokes on 2006-08-28
> **hype said:**
> Indeed, 
```
glxinfo | grep direct
direct rendering: No
``` 
But is it linked to the fact that, as sais in the how-to 
"Note for all cards: glxinfo will show that direct rendering is not working , don't worry that's normal when you are running XGL."

And actually most of plugins are working, were without 3D acceleration i just get a uber-slow crappy desktop; which is not (yet) the case here.
so the new features of XGL is for new hardware older hardware should use compiz-vanilla( you can install it in synaptic) so try this and let me know plz ;)

---

### Post by Jurgen272 on 2006-08-28
Tried both methods and no errors during install.
However cannot change themes with CGWD Themer.
When I click on a theme nothing happens.

Video Card : Ati Radeon 9600 (RV350 AR)

Anyone a suggestion or how to to make this work ?

---

### Post by chokes on 2006-08-28
> **Jurgen272 said:**
> Tried both methods and no errors during install.
However cannot change themes with CGWD Themer.
When I click on a theme nothing happens.

Video Card : Ati Radeon 9600 (RV350 AR)

Anyone a suggestion or how to to make this work ?
have you activated the theme in preferences of gnome-compiz-manager?

---

### Post by GregaS on 2006-08-28
Any howto's for KDE?

---

### Post by chokes on 2006-08-28
maybe later now we concetrate on gnome sorry

---

### Post by Jurgen272 on 2006-08-29
> **chokes said:**
> have you activated the theme in preferences of gnome-compiz-manager?

Yes, I checked both the checkboxes.
But when I select a theme nothing happens.

---

### Post by Ahriman on 2006-08-29
Same here, and after following both sections, I can't see a different in my desktop, other than the red icon in the tray.

---

### Post by balki2005 on 2006-08-29
hello,

I follow every step  without  problems, but when I reboot  nothing  changes ???

I don't have  any eye kindy  stuff. I can't use the  cube  and other compiz stuff :-(

who  can help me ??

I have  a  IBM Thinkpad T42

when  I checked  wiglxinfo:
jonay@thunderbird:~$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram,
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
jonay@thunderbird:~$

what  could  be the  problem ?

thanks  in advance,

balki2005

---

### Post by hype on 2006-08-29
Just a little edit: after new compiz update, i noticed real improvements from most plugin (especially cube rotate and scale, which are not choppy anymore)
 
But! As i told before, there were some issues using Opera. I think i "figured" out what the problem is.

 Actually, when i download a file using opera's download manager, XGL Cpu usage goes 90%.

 The funny thing is: if i display the "transferts" window in opera, Xgl goes 90% Cpu.
 But if i display anyother tab, Xgl goes back at normal usage (4% as im writing)
 Of course when download is finished everything goes back to normal.

 I think there are some more "situation" where Opera causes some Xgl Cpu highness; didnt figured out yet(maybe some javascript, but not sure tho).

---

### Post by chokes on 2006-08-29
> **balki2005 said:**
> hello,

I follow every step  without  problems, but when I reboot  nothing  changes ???

I don't have  any eye kindy  stuff. I can't use the  cube  and other compiz stuff :-(

who  can help me ??

I have  a  IBM Thinkpad T42

what  could  be the  problem ?

thanks  in advance,

balki2005
What is your video card?

---

### Post by balki2005 on 2006-08-29
my video card  is : (from  lspci)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

thanks in advance,

Balki2005

---

### Post by chokes on 2006-08-29
youre driver isnt installed corectly...  have you edited you file /etc/X11/xorg.conf   ?? and changed the driver to fglrx? if not this is your problem ;)

---

### Post by chokes on 2006-08-29
> **hype said:**
> Just a little edit: after new compiz update, i noticed real improvements from most plugin (especially cube rotate and scale, which are not choppy anymore)
 
But! As i told before, there were some issues using Opera. I think i "figured" out what the problem is.

 Actually, when i download a file using opera's download manager, XGL Cpu usage goes 90%.

 The funny thing is: if i display the "transferts" window in opera, Xgl goes 90% Cpu.
 But if i display anyother tab, Xgl goes back at normal usage (4% as im writing)
 Of course when download is finished everything goes back to normal.

 I think there are some more "situation" where Opera causes some Xgl Cpu highness; didnt figured out yet(maybe some javascript, but not sure tho).
  maybe its opera.... im using swiftfox and nothing like that....

---

### Post by balki2005 on 2006-08-29
I known  but  when  I  try  to change the driver  from  ati  to  fglrx.  then my  x-windows crashed.  maybe  I need  to  change  more ??

kind  regards,

Balki2005

---

### Post by chokes on 2006-08-29
> **balki2005 said:**
> I known  but  when  I  try  to change the driver  from  ati  to  fglrx.  then my  x-windows crashed.  maybe  I need  to  change  more ??

kind  regards,

Balki2005
do you have installed fglrx in synaptic?

---

### Post by chokes on 2006-08-29
> **Jurgen272 said:**
> Yes, I checked both the checkboxes.
But when I select a theme nothing happens.
ok try this in a terminal :

```
cgwd -replace
```

---

### Post by balki2005 on 2006-08-29
I think so,  with  apt-get  install  ....

---

### Post by chokes on 2006-08-29
> **balki2005 said:**
> I think so,  with  apt-get  install  ....
go in synaptic and search: fglrx if its installed and its not working i can't go further

---

### Post by balki2005 on 2006-08-29
ok  thanks  anyway  for youre help  !!!   ;-)

---

### Post by chokes on 2006-08-29
> **balki2005 said:**
> ok  thanks  anyway  for youre help  !!!   ;-) No problem ;)

---

### Post by toasted on 2006-08-29
What is the difference in the 2 methods? I don't see it written anywhere.
tia

---

### Post by S1NGH on 2006-08-29
> **toasted said:**
> What is the difference in the 2 methods? I don't see it written anywhere.
tia
the second section mainly focuses on the x series cards... but we are still testing with other cards, so if it works for you, please post your card too.

---

### Post by toasted on 2006-08-29
Ok I need to read some more but I think I will try it.
Im using an X1600

Its a little confusing though because at the **end** of the **first** section it says this:


> If you own an X series Radeon card , scroll down to the end of this HowTo!

That would tend to make me skip the second section altogether ya see.

So I should just do the 2nd and not the first.... right?

---

### Post by toasted on 2006-08-29
Sorry for the questions  LOL

At the end of the second section it says this:
> In the login manager you can now choose a session named Xgl. Answer to following question that you want to use XGL for this session only (if something went wrong you are logged in next time using standard session) If everything works fine , you can set it as the default session , remember you can always login a normal gnome session if you want.

So at gdm login a choice is presented to use XGL or normal. Is this true for the first method too?

---

### Post by chokes on 2006-08-29
> **toasted said:**
> Ok I need to read some more but I think I will try it.
Im using an X1600

Its a little confusing though because at the **end** of the **first** section it says this:




That would tend to make me skip the second section altogether ya see.

So I should just do the 2nd and not the first.... right?
yess youre right :)

---

### Post by chokes on 2006-08-29
> **toasted said:**
> Sorry for the questions  LOL

At the end of the second section it says this:


So at gdm login a choice is presented to use XGL or normal. Is this true for the first method too?
no the first section Xgl is loading with GDM and you dont have the choice to return back to a normal session

---

### Post by toasted on 2006-08-29
Well I had success! 
I am not able to use the new ATI drivers due to having the difficulties that a lot of people have. I'm still using the 8.26.18 drivers. Just thought I would mention that. Upgrade and I cannot run fglrx. 

Anyway, things open slow and happen slow when in xgl but they do happen. I was able to rotate the cube by clicking the switcher and have different things on different sides of the cube. I got the wobbly effect as well. 

Then I booted back into a Gnome session to make sure I can get back here with no trouble and did...  all seems normal here.

Time to go play some more!! Sure would be nice to have this same speed in XGL though!

---

### Post by thepahakurki on 2006-08-29
Thank you for the how-to but I'm also having problems with getting it to work. My videocard is ATI Radeon 9800 Pro.

I tried both ways to setup xgl but still nothing happens when I click on "Enable GL desktop" and select a skin.

I installed ATI drivers by following this how-to: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver)

glxinfo says direct rendering: yes

Can anyone help me?

---

### Post by chokes on 2006-08-29
> **thepahakurki said:**
> Thank you for the how-to but I'm also having problems with getting it to work. My videocard is ATI Radeon 9800 Pro.

I tried both ways to setup xgl but still nothing happens when I click on "Enable GL desktop" and select a skin.

I installed ATI drivers by following this how-to: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Installing_the_driver)

glxinfo says direct rendering: yes

Can anyone help me?

You should edit manually your xorg.conf and change (in section Device) the driver to fglrx

```
sudo gedit etc/X11/xorg.conf
```

---

### Post by thepahakurki on 2006-08-29
> **chokes said:**
> You should edit manually your xorg.conf and change (in section Device) the driver to fglrx

```
sudo gedit etc/X11/xorg.conf
```

Already did it and it still doesn't work... I must be doing something wrong now...

This is what it says 

```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

---

### Post by toasted on 2006-08-29
thepahakurki, what is the output of this when in normal Gnome session?
```
glxgears -printfps
```

You may want to try this install method. Its works for me and the newer drivers will not....

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)



Here is my output when running XGL (not bad!) Normal Gnome session I can get 5000 or so with the gear window covered up. 3900 or so with it wide open (visible)

In XGL it does not matter if the gears window is visible or covered up but moving a window around does cause the fps to drop although I dont know the effect of this in regular gnome session

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
17669 frames in 5.0 seconds = 3505.937 FPS
18194 frames in 5.0 seconds = 3636.326 FPS
18683 frames in 5.0 seconds = 3734.739 FPS
17932 frames in 5.0 seconds = 3568.956 FPS
18815 frames in 5.0 seconds = 3749.424 FPS
18945 frames in 5.0 seconds = 3771.351 FPS
18900 frames in 5.0 seconds = 3766.393 FPS
18847 frames in 5.0 seconds = 3755.036 FPS
18087 frames in 5.0 seconds = 3612.380 FPS
18480 frames in 5.0 seconds = 3694.638 FPS
18734 frames in 5.0 seconds = 3746.799 FPS
18813 frames in 5.0 seconds = 3747.062 FPS
18787 frames in 5.0 seconds = 3745.138 FPS
18760 frames in 5.0 seconds = 3747.944 FPS
16432 frames in 5.0 seconds = 3283.830 FPS -----------------
17324 frames in 5.0 seconds = 3441.728 FPS
17121 frames in 5.0 seconds = 3424.199 FPS moving a window around
16711 frames in 5.0 seconds = 3335.831 FPS -----------------
18815 frames in 5.0 seconds = 3762.156 FPS
18859 frames in 5.0 seconds = 3743.492 FPS
18815 frames in 5.0 seconds = 3746.983 FPS
18197 frames in 5.0 seconds = 3624.102 FPS

what does this mean?
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

BTW I run dual monitors

---

### Post by psb6m on 2006-08-29
I haven't been able to make it work: Installed by second method (since that looked safer); when I select "GL Desktop" all window decorations disappear, as if there were no window manager at all. Otherwise performance in xgl is very slow. I have:

 ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

and

fglrx 8.27.10-1_i386

Peter

---

### Post by chokes on 2006-08-29
> **toasted said:**
> thepahakurki, what is the output of this when in normal Gnome session?
```
glxgears -printfps
``` 
You may want to try this install method. Its works for me and the newer drivers will not....

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)



Here is my output when running XGL (not bad!) Normal Gnome session I can get 5000 or so with the gear window covered up. 3900 or so with it wide open (visible)

In XGL it does not matter if the gears window is visible or covered up but moving a window around does cause the fps to drop although I dont know the effect of this in regular gnome session

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
17669 frames in 5.0 seconds = 3505.937 FPS
18194 frames in 5.0 seconds = 3636.326 FPS
18683 frames in 5.0 seconds = 3734.739 FPS
17932 frames in 5.0 seconds = 3568.956 FPS
18815 frames in 5.0 seconds = 3749.424 FPS
18945 frames in 5.0 seconds = 3771.351 FPS
18900 frames in 5.0 seconds = 3766.393 FPS
18847 frames in 5.0 seconds = 3755.036 FPS
18087 frames in 5.0 seconds = 3612.380 FPS
18480 frames in 5.0 seconds = 3694.638 FPS
18734 frames in 5.0 seconds = 3746.799 FPS
18813 frames in 5.0 seconds = 3747.062 FPS
18787 frames in 5.0 seconds = 3745.138 FPS
18760 frames in 5.0 seconds = 3747.944 FPS
16432 frames in 5.0 seconds = 3283.830 FPS -----------------
17324 frames in 5.0 seconds = 3441.728 FPS
17121 frames in 5.0 seconds = 3424.199 FPS moving a window around
16711 frames in 5.0 seconds = 3335.831 FPS -----------------
18815 frames in 5.0 seconds = 3762.156 FPS
18859 frames in 5.0 seconds = 3743.492 FPS
18815 frames in 5.0 seconds = 3746.983 FPS
18197 frames in 5.0 seconds = 3624.102 FPS

what does this mean?
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

BTW I run dual monitors
XGL is using a part of opengl, its normal that youre results get worst and youre using the 3d on a dual monitor! think of that :P

---

### Post by toasted on 2006-08-29
There seems to be trouble with the switcher. When I view preferences, there is only 1 workspace shown. When I add workspaces there is no way to add the names to the workspaces. Only one workspace is named. In the switcher there are very small segments, one for each workspace, with the single name overlayed on all of the workspace segments. get it?  See the image. I named workspace one - Workspace One. The blue section under Wor is actual workspace one and under the rest of the name is where the additional workspaces reside. This is set to 4 workspaces

---

### Post by chokes on 2006-08-29
> **psb6m said:**
> I haven't been able to make it work: Installed by second method (since that looked safer); when I select "GL Desktop" all window decorations disappear, as if there were no window manager at all. Otherwise performance in xgl is very slow. I have:

 ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

and

fglrx 8.27.10-1_i386

Peter
Try compiz-vanilla it use less plugins and it light( your hardware is a litle old)

---

### Post by thepahakurki on 2006-08-29
> **toasted said:**
> thepahakurki, what is the output of this when in normal Gnome session?
```
glxgears -printfps
```

I used the command glxgears -info and got this
```
GL_RENDERER   = RADEON 9800 Pro Generic
GL_VERSION    = 2.0.5879 (8.26.18)
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture........
26137 frames in 5.0 seconds = 5227.214 FPS
26639 frames in 5.0 seconds = 5327.736 FPS
26824 frames in 5.0 seconds = 5364.698 FPS
26827 frames in 5.0 seconds = 5365.246 FPS
26832 frames in 5.0 seconds = 5366.369 FPS
26832 frames in 5.0 seconds = 5366.243 FPS
26838 frames in 5.0 seconds = 5367.572 FPS
26833 frames in 5.0 seconds = 5366.589 FPS
26840 frames in 5.0 seconds = 5367.810 FPS
26840 frames in 5.0 seconds = 5367.140 FPS
26845 frames in 5.0 seconds = 5368.987 FPS
26842 frames in 5.0 seconds = 5368.369 FPS
26841 frames in 5.0 seconds = 5368.200 FPS
26840 frames in 5.0 seconds = 5367.951 FPS
26846 frames in 5.0 seconds = 5369.200 FPS
26848 frames in 5.0 seconds = 5369.513 FPS
26852 frames in 5.0 seconds = 5370.266 FPS
26856 frames in 5.0 seconds = 5371.061 FPS
26856 frames in 5.0 seconds = 5371.188 FPS
26860 frames in 5.0 seconds = 5371.983 FPS
26866 frames in 5.0 seconds = 5373.119 FPS
26867 frames in 5.0 seconds = 5373.358 FPS
26874 frames in 5.0 seconds = 5374.653 FPS
26867 frames in 5.0 seconds = 5373.274 FPS
26872 frames in 5.0 seconds = 5374.309 FPS
26865 frames in 5.0 seconds = 5372.892 FPS
26871 frames in 5.0 seconds = 5374.141 FPS
26866 frames in 5.0 seconds = 5373.144 FPS

```

> **toasted said:**
> 
You may want to try this install method. Its works for me and the newer drivers will not....

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

Well I followed that and installed 8.26.18 drivers and still glx/compiz doesn't work...

---

### Post by chokes on 2006-08-29
> **toasted said:**
> There seems to be trouble with the switcher. When I view preferences, there is only 1 workspace shown. When I add workspaces there is no way to add the names to the workspaces. Only one workspace is named. In the switcher there are very small segments, one for each workspace, with the single name overlayed on all of the workspace segments. get it?  See the image. I named workspace one - Workspace One. The blue section under Wor is actual workspace one and under the rest of the name is where the additional workspaces reside. This is set to 4 workspaces
you have to change this setting in the preferences window of the compiz-manager (number of viewports)

---

### Post by toasted on 2006-08-29
> **thepahakurki said:**
> I used the command glxgears -info and got this



Well I followed that and installed 8.26.18 drivers and still glx/compiz doesn't work...

Your frame rates are comparable to mine and my card is an X1600!

I have to run with the gear window covered with another window to get the frame rate that high.

Another note-

I have the 686 smp kernel installed with hyper threading enabled in my bios. Dont know if that makes a difference or not.

P4 2.8
512 dual channel ram

Sorry but I cant answer why it doesnt work but im sure someone will :)

---

### Post by toasted on 2006-08-29
> **chokes said:**
> you have to change this setting in the preferences window of the compiz-manager (number of viewports)

Yes, mine is set to 4. In fact it will not go lower than 4 - the down arrow is greyed

This is some cool stuff though!!!!

---

### Post by toasted on 2006-08-29
Ok, another thing I noticed. 
I had set the workspace one name to "Workspace One" as shown in the pic
I did this while running XGL

I unchecked the box for gl desktop. It turned off. 
My desktop switcher reverted to the normal one with all 4 spaces named just as I had left it before in a normal Gnome session. Each one displayed its own name as normal and the size was larger as normal.

Then I ticked the gl desktop box again, xgl fired up and the switcher went back to displaying just the single name overlayed over the 4 narrow spaces. 

The name of workspace one reverted to my normal name as well. 

Follow?

---

### Post by chokes on 2006-08-29
just disable : show workspace name in switcher
and Xgl is testing software so it normal that its not perfect ;)

---

### Post by toasted on 2006-08-29
> **chokes said:**
> just disable : show workspace name in switcher
and Xgl is testing software so it normal that its not perfect ;)

LOL
I know that but you guys do want input I assume!!
Thats what beta is all about eh?

Disabling show names is ok, it gets rid of the name,  but there is no definition as to which space is what... no dividing lines between the spaces. 
More to ponder...  :mrgreen:

---

### Post by chokes on 2006-08-29
maybe it will be corect in the next realase of gnome ;)

---

### Post by psb6m on 2006-08-29
> **chokes said:**
> Try compiz-vanilla it use less plugins and it light( your hardware is a litle old)

Strange - I get the same result with compiz-vanilla.

Well, never mind. It was just whimsy to try this out; and at least I haven't broken anything!

Peter

---

### Post by erikcw on 2006-08-29
Hi all,

I tried installing using the second method, but something is not right.  XGL seems to load correctly, but compiz is not loading right.

Compiz loads, but won't let me switch virtual desktops.  Windows also don't have title bars or borders.

Here is some info about my system:

> 
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 2.0.6011 (8.28.8)


> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "dvorak,us"
        Option      "XkbOptions" "grp:shift_toggle"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "Buttons" "7"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "HP f2105"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

#Section "Device"
#       Identifier  "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
#       Driver      "fglrx"
#       Option      "VideoOverlay" "on"
#       Option      "OpenGLOverlay" "off"
#       BusID       "PCI:1:0:0"
#EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "KernelModuleParm" "agplock=0"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
#       Device     "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
        Monitor    "HP f2105"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection


> 
erik@turbo:~$ compiz --version
erik@turbo:~$ compiz 0.0.13.41


Can anyone tell me what I'm doing wrong?

Thanks so much!

---

### Post by chokes on 2006-08-29
> **erikcw said:**
> Hi all,

I tried installing using the second method, but something is not right.  XGL seems to load correctly, but compiz is not loading right.

Compiz loads, but won't let me switch virtual desktops.  Windows also don't have title bars or borders.

Here is some info about my system:







Can anyone tell me what I'm doing wrong?

Thanks so much!
have you rebooted youre machine?

---

### Post by psb6m on 2006-08-29
> **chokes said:**
> have you rebooted youre machine?

Can't speak for erikcw, but this was my problem exactly, and I did reboot my machine--several times.

Peter

---

### Post by erikcw on 2006-08-29
> **chokes said:**
> have you rebooted youre machine?

Yes, I've both rebooted and done a Ctrl+Alt+Backspace to resart X.  (when doing this sort of X configuration - doesn't Ctrl+Alt+Backspace achive the same effect as a full reboot?)

What else can I try?

Thanks!

---

### Post by tribaal on 2006-08-29
Just a sidenote for your (excellent) howto's writing:

Maybe you should rename section 1 and 2 to something more significant...
Like section one should probably be something like "Install compiz and run from gnome applet" and the second "Install compiz and start with a gdm menu entry" ? Just a thought...

Also, when using only section 2, you should mention the fact that it will run XGL on top of X, with an X session running in the background the shutdown/restart options in gnome will not be available. It is fixed if one follows section 1 though (then XGL is started by default, and it gets the rights to shutdown/restart or something).

A little issue I'm experiencing: once having followed both steps, my system starts up much much more slowly. After the usplash and the Ubuntu boot up process, I get stuck for about 25 seconds at the "X loading" step (when the background is nothing but a grey mess, like when X is booting), then the gdm login screen appears and everything works fast and nice.

Could this have to do with the following?
> 
    * Go to line 198 and change GdmXserverTimeout=10 to (this one is very crucial):

GdmXserverTimeout=50


Do you experience such a lag too? Is it normal? Is there anything I could do about it?

Cheers!

- trib'

---

### Post by S1NGH on 2006-08-29
> **tribaal said:**
> Just a sidenote for your (excellent) howto's writing:

Maybe you should rename section 1 and 2 to something more significant...
Like section one should probably be something like "Install compiz and run from gnome applet" and the second "Install compiz and start with a gdm menu entry" ? Just a thought...

Also, when using only section 2, you should mention the fact that it will run XGL on top of X, with an X session running in the background the shutdown/restart options in gnome will not be available. It is fixed if one follows section 1 though (then XGL is started by default, and it gets the rights to shutdown/restart or something).

A little issue I'm experiencing: once having followed both steps, my system starts up much much more slowly. After the usplash and the Ubuntu boot up process, I get stuck for about 25 seconds at the "X loading" step (when the background is nothing but a grey mess, like when X is booting), then the gdm login screen appears and everything works fast and nice.

Could this have to do with the following?


Do you experience such a lag too? Is it normal? Is there anything I could do about it?

Cheers!

- trib'
you could try it at 30 seconds, but i think that's the minimum you should go to. I dont have my ubuntu pc setup as yet... so i can't do some testing and debugging myself, but i will try and help and get more info on the current problems.

---

### Post by Sam on 2006-08-29
> **tribaal said:**
> After the usplash and the Ubuntu boot up process, I get stuck for about 25 seconds at the "X loading" step (when the background is nothing but a grey mess, like when X is booting), then the gdm login screen appears and everything works fast and nice.

I've got the same problem here :(

I've tried to change GdmXserverTimeout to several values, but it appears that the hangup time is always the same. And setting GdmXserverTimeout too low will result a GDM error...

Very odd.

---

### Post by toasted on 2006-08-29
Ive got the grey mess too but I dont think it lasts that long
Will have to time it

Its like a fine grid work of black and white blocks right?
Up close viewing is needed to see it
A bit away it looks grey and cursor is an X

Is this what you guys see?

---

### Post by tribaal on 2006-08-29
Yup that's it...
Really wonder what this can be. I thought GdmXserverTimeout was the answer, but since Sam tried it... :(

I'll look into the boot logs to see if something shows up there.

- trib'

---

### Post by toasted on 2006-08-29
Also, while we are raggin :mrgreen: 
hehe

In this link look at the compiz demo if you havent seen it
[http://www.ehomeupgrade.com/entry/2915/linux_xglcompiz_graphics](http://www.ehomeupgrade.com/entry/2915/linux_xglcompiz_graphics)

I havent been able to get my cube so I can see the top or bottom like this...
Has anyone?


Edit... heres some more LOL

I clicked preferences/ desktop (I think) 
enabled zoom 
After doing this compliz quit.
Unchecked the gl desktop box
checked it again and compliz restarted
Cannot run preferences again

I can repeat this at will it seems... need to log out and in or reboot

Edit
Nope have to reboot
log out and in works but functionality is not correct...

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Also, while we are raggin :mrgreen: 
hehe

In this link look at the compiz demo if you havent seen it
[http://www.ehomeupgrade.com/entry/2915/linux_xglcompiz_graphics](http://www.ehomeupgrade.com/entry/2915/linux_xglcompiz_graphics)

I havent been able to get my cube so I can see the top or bottom like this...
Has anyone?


Edit... heres some more LOL

I clicked preferences/ desktop (I think) 
enabled zoom 
After doing this compliz quit.
Unchecked the gl desktop box
checked it again and compliz restarted
Cannot run preferences again

I can repeat this at will it seems... need to log out and in or reboot

If you enabling windows effects or desktop/zoom water, compiz crashes, then what happens if you run the following in a terminal ?```
cgwd --replace &
```

---

### Post by tribaal on 2006-08-29
To show the top / bottom of the cube, you need to hold <ctrl><alt> and left mouse button, then move the mouse (while holding everything).

See? :)

- trib'

---

### Post by toasted on 2006-08-29
> **Sam said:**
> If you enabling windows effects or desktop/zoom water, compiz crashes, then what happens if you run the following in a terminal ?```
cgwd --replace &
```

I guess its just the zoom feature that made me think it crashed.
zoom makes all windows open at top left corner with no top bar available....
its weird


I see the top and bottom of the cube!!  SWEET! thanks 

How to place a different image there?
Also, is it possible to have different wallpaper on each side of cube?

---

### Post by Sam on 2006-08-29
> **toasted said:**
> How to place a different image there?
Also, is it possible to have different wallpaper on each side of cube?

Yes, you need gset-compiz to do that.

---

### Post by chokes on 2006-08-29
> **toasted said:**
> I guess its just the zoom feature that made me think it crashed.
zoom makes all windows open at top left corner with no top bar available....
its weird


I see the top and bottom of the cube!!  SWEET! thanks 

How to place a different image there?
Also, is it possible to have different wallpaper on each side of cube?

It have a plugin in developement for different wallpaper but its available for now

---

### Post by toasted on 2006-08-29
> **Sam said:**
> Yes, you need gset-compiz to do that.

to do wallpaper or the image?

---

### Post by toasted on 2006-08-29
> **chokes said:**
> It have a plugin in developement for different wallpaper but its available for now

development... hmmmmmmm if you knew what a rookie I was LOL
but if you want me to test I will

---

### Post by Sam on 2006-08-29
> **toasted said:**
> to do wallpaper or the image?

Top and bottom cube images. gset-compiz allows you to tweak a lot of options without using gconf-editor manually.

---

### Post by chokes on 2006-08-29
im not a developer ;)... its quinnstorm the developer of it im just using his repositories...

---

### Post by dude051 on 2006-08-29
I've been messing with XGL/Compiz on Ubuntu Dapper for a week or more now. And I just thought I would share some of my findings.

First off, XGL is oviously an OpenGL application, so if you are running the second method which runs XGL as a session on top of gnome you will not beable  to render OpenGL or XVideo well or even at all. If you go ahead and do:

```
fglrxinfo

and

fglrxinfo -display :0
```

You will see how XGL is running on display :1 and gnome on :0. Using this method you can also run the latest ATI drivers 2.28. But your performance of XGL will be top notch in favor of bad OpenGL/ XVideo rendering for other apps.

Following the first method, you are running XGL as the server. Because of this, you can run OpenGL and XVideo without a hitch. Try and run gxlgears using method 2, and then do on method 1. Depending on your card,  it should be much faster. The major downside with this, is if you are using any recent non-repository ubuntu drivers, ie ones you made, this option will not work. MESA drivers will always load in favor reguardless of your fglrx settings in xorg.conf. Obviously if you use the fglrx drivers through synaptic you should be fine.

Also, the grey checkard screen when starting up is normal. Ive been told by some developers over at the compiz forums that this is just XGL starting up and when using method 1, XGL as a server, it should never last more than about 25 or so seconds. The timeout will not effect this startup time, it is cpu/gpu dependant. If you set the timeout too low.. it will just error out XGL, thats because it just needs time to start.

One last thing heh, if you really want to harness the power of Compiz, do:

```
$ sudo apt-get install gconf-editor

$ gfconf-editor
```

Using this navigate to /apps/compiz/ . Here you can edit plugins and general config of compiz to do your bidding. If you want a cube similar to the above, you can change the images on top and below and the skydome. I did a post here on it: [http://www.ubuntuforums.org/showthread.php?t=243747]("http://www.ubuntuforums.org/showthread.php?t=243747")

Sorry I wrote so much... I dont think I forgot anything. But this is what I have had experience in.

---

### Post by toasted on 2006-08-29
> **Sam said:**
> Top and bottom cube images. gset-compiz allows you to tweak a lot of options without using gconf-editor manually.

Where would I find this? 
Is there a thread on the forum about it? 
I didnt check... guilty [-X

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Where would I find this? 
Is there a thread on the forum about it? 
I didnt check... guilty [-X

Synaptic, package **gset-compiz** ;)

An explaination of the settings is [here](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz).

---

### Post by toasted on 2006-08-29
Thanks for the info Dude!

> **dude051 said:**
> 
One last thing heh, if you really want to harness the power of Compiz, do:

```
$ sudo apt-get install gconf-editor

$ gfconf-editor
```



gfconf-editor
command not found

---

### Post by toasted on 2006-08-29
> **Sam said:**
> Synaptic, package **gset-compiz** ;)

An explaination of the settings is [here](https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz).

Actually I looked there first and its not in mine
Do I need a repository?

---

### Post by Sam on 2006-08-29
> **toasted said:**
> gfconf-editor
command not found

Typo, it was **gconf-editor**.

---

### Post by toasted on 2006-08-29
> **Sam said:**
> Typo, it was **gconf-editor**.

:) figured it out thanks

---

### Post by toasted on 2006-08-29
I looks like I need to place the image somewhere and then config to use it.
Where does the image go?

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Actually I looked there first and its not in mine
Do I need a repository?

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

---

### Post by toasted on 2006-08-29
This is fun!!

---

### Post by Sam on 2006-08-29
> **toasted said:**
> I looks like I need to place the image somewhere and then config to use it.
Where does the image go?

In gset-compiz, click the Images button, then add your images in "Top face" and "Bottom face". Move your images to the top of the list to use them.

In "Plugins" button, "Cube" tab, you can scale the images to fit the surface.

---

### Post by toasted on 2006-08-29
I was talking about the gconf-editor..... i'm headed for your program now, should be easier. Thanks again!!!

---

### Post by toasted on 2006-08-29
Sam,
I added that repository to my sources.list
Opened Synaptic
Clicked refresh
Still no program showing

---

### Post by erikcw on 2006-08-29
I followed the first method this time, and nothing is happening.  When I click "GL Desktop" in the red cube a checkmark appears, and nothing happens.  Shouldn't this be sarting compiz?

Thanks!

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Sam,
I added that repository to my sources.list
Opened Synaptic
Clicked refresh
Still no program showing

Oops... You're right it's no more in the repository...

Download the deb file [here](http://ubuntuforums.org/showpost.php?p=1402545&postcount=6)


EDIT: Don't use gset-compiz, it's [outdated](http://ubuntuforums.org/showpost.php?p=1438690&postcount=104) !

---

### Post by tribaal on 2006-08-29
> 
I followed the first method this time, and nothing is happening. When I click "GL Desktop" in the red cube a checkmark appears, and nothing happens. Shouldn't this be sarting compiz?


Well it should... 
The transition between the two is not noticeable (or barely).

Try to hold <ctrl><alt> and the left mouse button and move the mouse with the checkbox ticked.

Notice anything?

-trib'

---

### Post by toasted on 2006-08-29
> **Sam said:**
> Oops... You're right it's no more in the repository...

Download the deb file [here](http://ubuntuforums.org/showpost.php?p=1402545&postcount=6)

up and running Sam, thanks a bunch!!

---

### Post by psb6m on 2006-08-29
> **psb6m said:**
> Can't speak for erikcw, but this was my problem exactly, and I did reboot my machine--several times.

Peter

I got this going on my desktop machine (a different ATI card) via method 2. Method 1 didn't work for some reason: Xgl never started, but just X. Yet I double checked my configuration files: I'm sure I followed the instructions exactly. Any idea of what might have gone wrong?

Oh yes, and -- it's very pretty!

Peter

---

### Post by erikcw on 2006-08-29
> **tribaal said:**
> Well it should... 
The transition between the two is not noticeable (or barely).

Try to hold <ctrl><alt> and the left mouse button and move the mouse with the checkbox ticked.

Notice anything?

-trib'

No, nothing.  I had it working on the same machine on Sunday - but I did a reformat and now I can't get it working.

> 
erik@turbo:~$ ps aux | grep compiz
erik      5714  0.0  1.0  32704 10652 ?        Ss   16:21   0:00 compiz-tray-icon
erik     10189  0.0  0.0   2876   796 pts/1    R+   16:58   0:00 grep compiz
erik@turbo:~$


How do I know if method one is loading XGL correctly?  It isn't showing up in ps either...

Thanks!

---

### Post by toasted on 2006-08-29
> **Sam said:**
> In gset-compiz, click the Images button, then add your images in "Top face" and "Bottom face". Move your images to the top of the list to use them.

In "Plugins" button, "Cube" tab, you can scale the images to fit the surface.

Cant say why this is but..
I added my images, same one for top and bottom
I deleted the novell images
Reboot and novell image is still showing
In program my image is the only one showing still

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Cant say why this is but..
I added my images, same one for top and bottom
I deleted the novell images
Reboot and novell image is still showing
In program my image is the only one showing still

I had this problem only with jpeg files. Convert your images to png.

---

### Post by toasted on 2006-08-29
Actually they are .png
When browsing for images .png are the only ones that show up
jpg or gif just are not shown in the browser window

---

### Post by Sam on 2006-08-29
> **toasted said:**
> Actually they are .png
When browsing for images .png are the only ones that show up
jpg or gif just are not shown in the browser window

That's weird. Are the settings well stored in gconf-editor, keys /apps/compiz/plugins/cube/screen0/options/images_bottom and images_top ?

If you change some another random settings, do the changes apply ?

---

### Post by dude051 on 2006-08-29
> **Sam said:**
> That's weird. Are the settings well stored in gconf-editor, keys /apps/compiz/plugins/cube/screen0/options/images_bottom and images_top ?

If you change some another random settings, do the changes apply ?

Sorry I forgot to add, gset-compiz is no longer developed and is outdated. All the options may or may not work on current compiz builds. This is why it is not in the repositories and also why I recommend gconf-editor.

Sorry about my first post, it was a typo heh.

---

### Post by Sam on 2006-08-29
> **dude051 said:**
> Sorry I forgot to add, gset-compiz is no longer developed and is outdated. All the options may or may not work on current compiz builds. This is why it is not in the repositories and also why I recommend gconf-editor.

Sorry about my first post, it was a typo heh.

Thanks for the info, it's nice to know.

---

### Post by toasted on 2006-08-29
> **Sam said:**
> That's weird. Are the settings well stored in gconf-editor, keys /apps/compiz/plugins/cube/screen0/options/images_bottom and images_top ?

If you change some another random settings, do the changes apply ?

I found the trouble, and the forum was down for a while for me.
I was running with gksudo so any changes I was making was for root I guess. Anyway I removed it and it works great now!!

Havent figured out how to do wallpaper yet.

Dude, too bad this prog was let go.. its pretty nice and easy to use once you get it going

---

### Post by dude051 on 2006-08-29
It was a very nice program, made it very easy. They may update it someday, but right now compiz is exploding on the scene with new features and plugins. So the best way it direct config editing through gconf-config.

As for the wallpaper, I think you are talking about the skydome.

Do this:

Open gconf-editor
Goto /apps/compiz/plugins/cube/screen0/options
Scroll down check skydome and skydome_animated (this makes the the skydome move around the cube)
And under skydome enter the path to a picture that is width/2 x length/2 atleast. For some skydome pictures try: [http://www.compiz.net/topic-10-skydome-images]("http://www.compiz.net/topic-10-skydome-images")

---

### Post by mnementh666 on 2006-08-29
Got it running, using the second method.  NICE :D 
Second attempt at getting Xgl/Compiz running, first one failed, unsure why, didn't delve into it too much.
I have a couple of questions about Xgl/Compiz, but I'll post those elsewhere. 

FWIW, my setup follows:
HP Pavilion a1230n, Athlon64 3700+, ATI Xpress200 RS480 IGP
ATI driver 8.27.10, custom 2.6.17.7 32bit kernel.

Of course, XFCE is faster, but definitely not as pretty ;)

Big thank you goes to the writer of the howto! =D>

---

### Post by toasted on 2006-08-29
> **dude051 said:**
> It was a very nice program, made it very easy. They may update it someday, but right now compiz is exploding on the scene with new features and plugins. So the best way it direct config editing through gconf-config.

As for the wallpaper, I think you are talking about the skydome.

Do this:

Open gconf-editor
Goto /apps/compiz/plugins/cube/screen0/options
Scroll down check skydome and skydome_animated (this makes the the skydome move around the cube)
And under skydome enter the path to a picture that is width/2 x length/2 atleast. For some skydome pictures try: [http://www.compiz.net/topic-10-skydome-images]("http://www.compiz.net/topic-10-skydome-images")

I'm thinking the skydome is like the background stationary image when you are spinning the cube around. I was talking more in the lines of having a different wallpaper on each side of the cube... so I must have endless resources eh? Ride it hard and put it away wet... thats what I always say! LOL

I could not seem to locate /apps/compiz/plugins/cube/screen0/options

nevermind... I need to learn to read  LOL

Edit:
Skydome and skydome animate were already checked. You can select them in preferences from the panel icon. I see that you can now select the top and bottom images there as well. That must have been what the update was earlier today. I swear the top and bottom were not there...

**[COLOR="DarkRed"][SIZE="4"]Edit again[/SIZE][/COLOR]**
I don't find where wallpaper can be config'd 
Guess that gives us something to look forward to eh?
:mrgreen:

---

### Post by pyxu619 on 2006-08-29
Thnx!! the second method works but I need to add in 
```
 gconftool-2 --set --type boolean /apps/panel/global/enablemations "False"
```
in order to but to not get black borders.

:KS :KS :D

---

### Post by dude051 on 2006-08-30
> **toasted said:**
> 
Edit:
Skydome and skydome animate were already checked. You can select them in preferences from the panel icon. I see that you can now select the top and bottom images there as well. That must have been what the update was earlier today. I swear the top and bottom were not there...

**[COLOR="DarkRed"][SIZE="4"]Edit again[/SIZE][/COLOR]**
I don't find where wallpaper can be config'd 
Guess that gives us something to look forward to eh?
:mrgreen:

As far as I know, this would not be something controlled by XGL. As XGL does render the 3D aspect of the virtual desktops, its nothing new for linux as a whole. So my guess would be that this would have to be changed through Ubuntu.. but i've never done that or heard of it being done heh.

---

### Post by tribaal on 2006-08-30
I'm having a little concern:

I noticed the right-clicking on a window's frame sometimes brings up a "decoration" menu allowing me to set a particular window's transparency or shading for example, similar to the "move to desktop number..." option.

But the problem is: it only is available *sometimes*. And I couldn't find when or what makes it appear/disappear...

Anybody have any idea?

- trib'

---

### Post by S1NGH on 2006-08-30
Hey guys, thanks for the more feedback, i will check with chokes the problems which some of you are experiencing... i am still getting to know more about xgl and learning too :) once we get most of the problems sorted out, we will release a final guide, any contibutions, additions you want to be seen on the guide are all welcomed, tips and tricks are also welcome, you will be credited for the work etc, we just want to make one big good looking guide for xgl/compiz ;)

---

### Post by tribaal on 2006-08-30
I'll definately give you all the feedback I can :)

As soon as possible I'll install Ubuntu on my last crippled machine, and from there XGL/Compiz of course. Except for a few little inconsistencies (see my posts above), averything seems to run fine on my laptop.

And your tutorial rocks :)

- trib'

---

### Post by toasted on 2006-08-30
Yes the tutorial is working well it seems. As Tribal noted a few pages ago though, you really do need to be more specific on what the difference is between the 2 different methods to install. The first will not offer a choice at boot and the second one will. The first will not let you have a normal Gnome session. The first will probably operate faster.... etc. 

Speaking of that, has anyone compared the two with any sort of benchmarks?
It seems stable enough to me to want to remove this one and install the first method. I do like having the choice though. It also seems good that you used aptitude. Speaking of that, it might not be a bad idea to tell how to uninstall this in case people change their minds and want to try the other method (like me) :)  How-to's never tell how to uninstall so you guys can break new ground here!

I installed this little game the other day called abuse. When I start this game up under xgl/compliz the window is so transparent I cannot see to play the game (no loss really). Right clicking the top bar brings up the opacity menu and it is already set to 100%. 

I also tried enemy territory. The opacity is fine with this. Normally though when you open ET it takes over my primary monitor... using up all the real estate with no frame - no sign that it is running in a window. While running xgl/compliz though it is windowed. The terminal starts up first on my primary monitor - centered. Then ET starts up in a window to the right of the terminal window, actually touching it. The game window is centered between the 2 monitors. What I have to do is hurry and minimize the terminal window and grab the ET window before the mouse is lost in the game and I have no screen functionality. I can drag it over to the primary monitor and am able to use it, but it cannot be maximized. It's playable I guess but it is less than ideal. 

I realize that xgl/compliz is running on top of X and this must be the reason. Just reporting my findings is all.

---

### Post by mrojas73 on 2006-08-30
This guide is very well done,  I however have the infamous ati 200M card and it takes many reboots to be able to login due to hardlocks.  No problems at all using a regular gnome session or with compiz once I am able to login. I wonder how many of you using this graphics card are experiencing this problem?

---

### Post by misha680 on 2006-08-30
I had to install an old version of Xgl, and then things worked beautifully on my ATI Mobility Radeon 9000. I uploade the old Xgl deb to my compiz bug report. You can find the deb here:

[http://bugs.compiz.net/file_download.php?file_id=12&type=bug](http://bugs.compiz.net/file_download.php?file_id=12&type=bug)

Once you install it, just do Package/Force Version in Synaptic to make sure it doesn't get updated.

Misha

---

### Post by thepahakurki on 2006-08-30
I just got xgl/compiz working but not with this how-to.
Earlier I had trouble not getting it work by following this how-to.

However I did a clean reinstall of Ubuntu, then installed ATI drivers with this script: [http://ubuntuforums.org/showthread.php?t=235145](http://ubuntuforums.org/showthread.php?t=235145)

And the I installed xgl and compiz by following these how-to's:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

And damn does my desktop look good!

---

### Post by colonelk on 2006-08-30
Excellent tutorial.  Works perfectly on a vanilla Ubuntu 6.06 Dapper with the latest ATI Drivers 8.28.8 installed first.

The cgwd themes even work as they are supposed to also.

:D

---

### Post by chokes on 2006-08-30
ok i edited litlle bit the how to to explain the difference of one to other
Please let me know if something wrong ;)

---

### Post by sjust on 2006-08-30
HI I installed by using the second methode, I use Gnome to play games. Everything worked great I love what this has done to my desktop I do not miss XP at all and will not miss Vista either.

---

### Post by S1NGH on 2006-08-30
> **chokes said:**
> ok i edited litlle bit the how to to explain the difference of one to other
Please let me know if something wrong ;)
good job and thanks, i will search for some updates that can be made without hurting user's compatibility issues'.
> HI I installed by using the second methode, I use Gnome to play games. Everything worked great I love what this has done to my desktop I do not miss XP at all and will not miss Vista either.
Great! glad to hear that.

---

### Post by toasted on 2006-08-30
**This is ok now**


**Second section removal:**

update repositories:
```
  sudo gedit /etc/apt/sources.list
```

Comment (#) out the following or delete:
```

#deb http://www.beerorkid.com/compiz dapper main aiglx 
#deb http://media.blutkind.org/xgl/ dapper main aiglx 
#deb http://ubuntu.compiz.net/ dapper main aiglx
```

remove packages  
```
 sudo aptitude remove xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes
```


Remove start up script and XGL session for login manager

Delete: 

```
sudo rm /usr/bin/startxgl.sh
sudo rm /usr/share/xsessions/xgl.desktop
```

reboot

---

### Post by Frostmourne on 2006-08-30
I am confused about the repositories. Why do they have aiglx in them, if the tutorial is for XGL? Shouldn't it just be:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

---

### Post by W.McL on 2006-08-30
> **misha680 said:**
> I had to install an old version of Xgl, and then things worked beautifully on my ATI Mobility Radeon 9000. I uploade the old Xgl deb to my compiz bug report. You can find the deb here:

[http://bugs.compiz.net/file_download.php?file_id=12&type=bug](http://bugs.compiz.net/file_download.php?file_id=12&type=bug)

Once you install it, just do Package/Force Version in Synaptic to make sure it doesn't get updated.

Misha

Had to do the same to get compiz working on my Mobility Radeon 9000 (with fglrx-driver version 8.28.8 )
I used the second method.

---

### Post by toasted on 2006-08-30
> **tribaal said:**
> I'm having a little concern:

I noticed the right-clicking on a window's frame sometimes brings up a "decoration" menu allowing me to set a particular window's transparency or shading for example, similar to the "move to desktop number..." option.

But the problem is: it only is available *sometimes*. And I couldn't find when or what makes it appear/disappear...

Anybody have any idea?

- trib'

Every time I have checked mine it was ok... sorry thats no help I know

---

### Post by chokes on 2006-08-30
> **Frostmourne said:**
> I am confused about the repositories. Why do they have aiglx in them, if the tutorial is for XGL? Shouldn't it just be:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

its because gnome-compiz-manager are in aiglx repository

---

### Post by toasted on 2006-08-31
I have had windows start to move a little off the screen at the top to a point where the bar is not reachable. Then I could not move the window back down where it was supposed to be. If this happens to you, heres a tip:

Right click the entry for this window in the taskbar and choose 'move'
When you get it where you want it, hit escape to stop moving

Works good!

---

### Post by chokes on 2006-08-31
> **toasted said:**
> I have had windows start to move a little off the screen at the top to a point where the bar is not reachable. Then I could not move the window back down where it was supposed to be. If this happens to you, heres a tip:

Right click the entry for this window in the taskbar and choose 'move'
When you get it where you want it, hit escape to stop moving

Works good!
You can just press ALT + Left click ;)

---

### Post by toasted on 2006-08-31
Removal for the first method -

----------------------

Prepare and update repositories:
```
sudo gedit /etc/apt/sources.list
```

Remove or comment out (#) quinstorms' and reggaemanus' repositories to /etc/apt/sources.list:
```
#deb http://www.beerorkid.com/compiz dapper main aiglx 
#deb http://media.blutkind.org/xgl/ dapper main aiglx 
#deb http://ubuntu.compiz.net/ dapper main aiglx
```

Remove instaled packages:
```
sudo aptitude remove xserver-xgl compiz compiz-core compiz-plugins compiz-gnome gnome-compiz-manager cgwd cgwd-themes
```

Modify /etc/gdm/gdm.conf-custom:
```
  sudo gedit /etc/gdm/gdm.conf-custom
```

Look for [servers] section and delete this:
```
servers] # Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX).
1=Xgl 

[server-Xgl]  name=Xgl server  command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer 
flexible=true
```

Modify /etc/gdm/gdm.conf :
```
  sudo gedit /etc/gdm/gdm.conf
```

    * And change:



```
#0=Standard 
1=Standard
```

to

```
0=Standard 
#1=Standard
```

reboot

---

### Post by chokes on 2006-08-31
ok it updated!!!:) so it have an howto for removal the two section tanx to toasted!!!!;)

---

### Post by kosmic on 2006-08-31
Ok When I have XGL+Compiz running and press "SHIFT + BACKSPACE" Gnome reboots to the GDM login.

Also I can't make the @ symbol :(

Anyone knows how to solve this 2 problems ??

Thanks

---

### Post by kosmic on 2006-08-31
Ok I've found the solution, just do in terminal

xmodmap /usr/share/xmodmap/xmodmap.YourCountryCode.

Ex.:
xmodmap /usr/share/xmodmap/xmodmap.pt

---

### Post by ericesque on 2006-09-01
no dice.   

I get the red cube, but like others, checking the GL Desktop doesn't do anything.  Every time I go to preferences, the Enable GL Desktop is unchecked again.  Also, each time I do check the Enable GL Desktop, the window decorations change (assumably to the Compiz theme) but switch right back... blarg.

---

### Post by chokes on 2006-09-01
> **ericesque said:**
> no dice.   

I get the red cube, but like others, checking the GL Desktop doesn't do anything.  Every time I go to preferences, the Enable GL Desktop is unchecked again.  Also, each time I do check the Enable GL Desktop, the window decorations change (assumably to the Compiz theme) but switch right back... blarg.
wichone of the section have you followed?

---

### Post by Gomer19 on 2006-09-01
> **ericesque said:**
> no dice.   

I get the red cube, but like others, checking the GL Desktop doesn't do anything.  Every time I go to preferences, the Enable GL Desktop is unchecked again.  Also, each time I do check the Enable GL Desktop, the window decorations change (assumably to the Compiz theme) but switch right back... blarg.

I have got it too, followed section 1 and 2.

Isnt there any way to take a look to log files of compiz / GL Desktop? Just for debugging.

---

### Post by toasted on 2006-09-01
I finally tried the first method. I have 2 Ubuntu installs. This method does not seem to work for me. 

I get this from - compiz --version
```
compiz 0.0.13.41
```

On initial install it did not work. I did the updates that the system said were there...  17 of them I think. That did not change anything. 

When I click the icon, Initially the Gl Desktop checkbox was unchecked. Checking that did nothing. Bringing up preferences showed the "Enable GL Desktop" checkbox was unchecked. I checked that. Close the configurator and open it again... the box is unchecked again. 

It is then that I discovered that opening the preferences unchecks the box in the icon's menu too. 

It seems that compliz is installed but just not functioning. I have 5000+ fps in glx gears and fglrx is working good. 

Any thoughts? I think this has happened to others too.

---

### Post by toasted on 2006-09-01
OOPS posted that too soon
I thought the video was ok but...
when I do fglrxinfo it says
```
Error: unable to open display :0
```
Now, before I installed it told me that the drivers were correct
Actually, now the glxgear speeds are higher than they were... thats odd

---

### Post by toasted on 2006-09-01
Maybe I should not post this here but....
I uninstalled using the uninstall method... which worked fine btw
Then I installed again using this:
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
That one worked fine...  must be an older version?

There is no icon to turn it on and off though so thats a bummer

---

### Post by toasted on 2006-09-01
This method seems a bit faster too. Not a lot, but maybe a little. Its close but this has the edge I think.

XGL is not running on top of X so there must be fewer resources used. FPS in glxgears is near normal whereas it was 10% or so less in the second method. 

This is a 386 kernel too so that makes some difference. Here is a screen shot of system monitor of this install and I will post the same from the other install - 686 kernel and XGL running on top of X witn no hyperthreading.

---

### Post by toasted on 2006-09-01
It's lonely here tonight! LOL
Here is a screenshot of system monitor from the second method install. 

Another thing I noticed....
This install on boot.. the grey yucky screen lasts only 10 seconds where the other one lasts nearly 30 seconds while XGL loads.

I checked glxgears again
This install is 3840 fps or so
The other install is 3960 or so
Not that much difference I guess.

What is odd is post 137. That was my failed install where XGL ws working but compliz was not. There I was getting well over 5000 fps in glxgears!

---

### Post by airwolf on 2006-09-01
I pretty much have the same kind of problem like some of the people that have posted in this thread. XGL loads fine but there seems to be a problem with compiz. When I enable GL Desktop all of my window decorations disappear and none of the plugins seems to work. 

I followed the second method and have an ATI Radeon 9250. Is there anything that I can do to solve this?

Any help will be appreciated. Thanks.

---

### Post by chokes on 2006-09-02
its normal that the gnome compiz-manager isnt woring because it in heavy developenment if it not working you can alway take the script (ill add it when ill make the final how to)

---

### Post by chokes on 2006-09-02
> **airwolf said:**
> I pretty much have the same kind of problem like some of the people that have posted in this thread. XGL loads fine but there seems to be a problem with compiz. When I enable GL Desktop all of my window decorations disappear and none of the plugins seems to work. 

I followed the second method and have an ATI Radeon 9250. Is there anything that I can do to solve this?

Any help will be appreciated. Thanks.

have you tried this?
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by phoqueyoo on 2006-09-02
nevermind

---

### Post by airwolf on 2006-09-02
> **chokes said:**
> have you tried this?
[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Yes, I did try that last night as well and the same thing happens. Any other ideas?

Thanks.

---

### Post by chokes on 2006-09-02
> **airwolf said:**
> Yes, I did try that last night as well and the same thing happens. Any other ideas?

Thanks.
your video driver is correctly installed?

---

### Post by airwolf on 2006-09-02
> **chokes said:**
> your video driver is correctly installed?

I believe so. Results from a normal gnome session:

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
```

glxinfo | grep render```

direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9200 Series DDR Generic
```

---

### Post by chokes on 2006-09-02
maybe you can try with a fresh install ????

---

### Post by Webspot on 2006-09-03
-

---

### Post by Webspot on 2006-09-03
-

---

### Post by Webspot on 2006-09-03
Followed the both sections and both didn't work.

The first one loaded up gnome fine. But when right clicking on gnome-compiz-manager and selecting GL Desktop, the gnome window decorations disapear for a second and then come back with no compiz at all.

On the second section, I followed it exactly and selected Xgl from the sessions and logged in. Nothing happens for a few seconds, and then an error message pops up saying that the session only lasted 10 seconds. This error message also refered me to .xsession-errors. The content of .xsession-errors is below:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "andrew"
/etc/gdm/Xsession: Beginning session setup...

Fatal server error:
no screens found

(gnome-session:6262): Gtk-WARNING **: cannot open display:  

```

Please help!

*There seems to be some strange triple post thing just happened above. Could a mod clear this up*

---

### Post by joemeca on 2006-09-03
yup neither of the ways worked i have tried both on fresh installs and get same problem as other guys.  So if you are going to do this DONT!  untill it gets updated.

---

### Post by VanS on 2006-09-04
Hi, first off am pretty new to Ubuntu, but I have played with Linux in the past.

Now that that is out of the way, I have some feedback about this Compiz Beta:

System Info:
HP Pavilion zv6000
AMD Athlon 64 3200
ATI Radeon XPRESS 200M (Sideport Memory Disabled / 128 MB UMA)
768 MB Total Memory (640 available after UMA)
ATI Driver Version 2.28.8

My thoughts:
This is a really cool interface that is actually has great function as well as form.

Bugs: 
I don't know if any of these have been brought up before...skimmed the thread to check, but at least you'll know that they occur on my hardware.

- When I push shif+backspace, X-server crashes back to the login screen
- When I launch an app from a panel, the background of the screen starts freaking out, lots of scrambled pixels and artifacts.  When the app is finished launching and the screen refreshes, everything is fine.
- Something similer to the above happens when I push the System Quit button to logout.

It runs suprisingly smoothly, considering that this *is* a laptop.  I hope that ATI comes out with updated drivers so I can utilize my sideport memory.

I'll let you know if anything else comes up.

---

### Post by tribaal on 2006-09-04
> - When I push shif+backspace, X-server crashes back to the login screen

Hum well actually shift + backspace is the keyboard shortcut to kill the X server... It's it's expected behavior :)

- trib'

---

### Post by tribaal on 2006-09-04
hi all!

The latest updates seem to have messed up my Compiz behavior: the window borders aren't drawn anymore, and my plugins (like the cube) don't work anymore...

Something in the latest Beerorkid release seem broken.

Edit: Now ticking the "GL desktop" think in the compiz tray icon doesn't change anything anymore. I'm stuck with a normal gnome session... Anybody else experiencing the same problem?

Anybody know how to revert / fix this?

- trib'

---

### Post by jeremytaylor on 2006-09-04
I have this problem too. any suggestions?
jeremy

---

### Post by Perkabalo on 2006-09-04
Tried both, doesn't work. :'(

Card: Radeon 9600 PRO, RV350

Driver version: 8.27.10

Hopefully it will in the future :)

---

### Post by SvanteH on 2006-09-04
Runs quite smooth on my computer, sadly Cedega doesn't run properly under it.

---

### Post by originof on 2006-09-04
> **tribaal said:**
> hi all!

The latest updates seem to have messed up my Compiz behavior: the window borders aren't drawn anymore, and my plugins (like the cube) don't work anymore...

Something in the latest Beerorkid release seem broken.

Edit: Now ticking the "GL desktop" think in the compiz tray icon doesn't change anything anymore. I'm stuck with a normal gnome session... Anybody else experiencing the same problem?

Anybody know how to revert / fix this?

- trib'

i've this problem too :-|


EDIT : Type in terminal compiz-start

---

### Post by tribaal on 2006-09-04
Follow indications found in [ here ]("http://ubuntuforums.org/showpost.php?p=1460710&postcount=11"), it'll fix it.

- trib'

---

### Post by chokes on 2006-09-04
yeah i know that the update of today has broke compiz it because quinn are making an alternative for gconf to store the plugins setting.... so gnome-compiz-manager is useless for now.....(i think it will be updated soon) if you want to change the plugins settings type csm in a terminal ;)

---

### Post by toasted on 2006-09-06
Here is a replacement icon. the old one no longer is needed. 
Follow along:

Credit to cyberorg
[http://www.compiz.net/topic-1170-3.html](http://www.compiz.net/topic-1170-3.html)

> 
1. Download the script, rename it to compiz-start.py and place it in /usr/bin or any of your bin path. 

2. chmod +x /path/to/compiz-start.py

3. Download logo file and place it in /usr/share/compiz/logo24.png
(right click - save image)

4. You need the very latest compiz-quinn packages for this to work. Make sure you have cgwd in your bin path (/usr/bin/cgwd or equal) make sure it has executable permission.

5. If you are using packages from opensuse compiz-quinn repository, do not download this, as it is already in the package all set up.

6. Now it will run cgwd by default if available. If cgwd is not available it will start gwd.

For all the folks who didnt know, cgwd probably works with compiz vanilla too, so does this script.


Add /usr/bin/compiz-start.py  in your system/sessions/startup programs
disable any other startup scripts you have in there

---

### Post by swmiller6 on 2006-09-08
Ok I have used the second method. At first everything appears to be working.. The tool tips pop up all wobbly and I  can get the cube and rotate from one desktop to the next.. But as soon as I try to open the file browser everything crashes and I and end up back on the login screen, if I login with out rebooting my computer things even in a normal session do not work right.

here are the thing I thought to may need to know, If I forgot something please let me know.
```
swmiller6@swmiller6-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
``` 

xorg.conf 
```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "KernelModuleParm" "agplock=0"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "KernelModuleParm" "agplock=0"
EndSection
```

```
swmiller6@swmiller6-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ARB_draw_buffers, GL_ATI_draw_buffers,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

---

### Post by detectiveinspekta on 2006-09-10
First Method:
```

 GdmXserverTimeout=50   doesn't exist

```

Second Method:
I can get through it all, reboot, choose XGL as next session, thing seem to be running as usuall. Open any program and there is no window around it. The Red icon in the notification bar doesn't appear.

Also GDM contains Xgl and XGL, must be my fault from prevous attempts to get xgl working.

---

### Post by S1NGH on 2006-09-10
> **detectiveinspekta said:**
> First Method:
```

 GdmXserverTimeout=50   doesn't exist

``` 
Second Method:
I can get through it all, reboot, choose XGL as next session, thing seem to be running as usuall. Open any program and there is no window around it. The Red icon in the notification bar doesn't appear.

Also GDM contains Xgl and XGL, must be my fault from prevous attempts to get xgl working.

try uninstalling it with the guide, then reinstall it, first have a look at what the methods do and choose your choice from there.

---

### Post by W.McL on 2006-09-19
Sorry for this Post, I was the reason for the problem myself by forgetting to reinstall the proprietary ATI drivers after an kernel update, so 3D-accelleration didn't work and compiz of course too.

---

