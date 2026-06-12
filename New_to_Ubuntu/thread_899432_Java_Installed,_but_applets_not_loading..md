---
title: "Java Installed, but applets not loading."
date: 2008-08-24
forum: New to Ubuntu
---

### Post by agraano on 2008-08-24
I have got the Sun Java Installed (Runtime). 

When I go to [http://www.java.com/en/download/help/testvm.xml?ff3](http://www.java.com/en/download/help/testvm.xml?ff3), it says, the JVM is working, however, when I go to another website(s), it doesn't work - I mean, the applets, do not load.

Eg: [http://www.indiabulls.com/equities/techanalysis/tech_analysis.asp](http://www.indiabulls.com/equities/techanalysis/tech_analysis.asp). This webpage, uses an applet. Firefox browser states - Java Applet Failed.

System Info:

1. I am using Intel Pentium D Processor, with 1 Gig of physical memory.
2. When I do Java -version, I get the following

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

Have attached the snapshot of java installation in Add / Remove Programmes.

Appreciate any help in this regard.

Thanks,
Anoop.

---

### Post by imon9 on 2008-08-24
did u have sun-java plugin (for browser) installed?
sudo apt-get sun-java6-plugin sun-java6-jre sun-java6-bin

---

### Post by oooh on 2008-08-25
Same problem here. However, I can properly see youtube, but can not use the JAVA applications in facebook.

I have installed:
sun-java6-jre 
and all dependancies

I dont find sun-java6-plugin in the repositories

JRE is installed, but not listed in about:plugins in firefox.

By the way , I am using Sony Vaio 64bits

---

### Post by zamadatix on 2008-08-25
64 bit ocmptures (such as mine) dont have a full java for linux. some applets wrok otehrs wont load, i beleive sun is still working on it. you can install a 32 bti browser but i never did all the work for it myself 9dont use them much)

---

### Post by Thelasko on 2008-08-25
Make sure you don't have any other versions of Java installed, like OpenJDK or GCJ.

---

### Post by LowSky on 2008-08-25
sudo apt-get install ubuntu-restricted-extras

it should work, mine is!

If not uninstall firefox install the 32bit version and then things should work

---

### Post by agraano on 2008-08-26
Hello,

Thanks to all for the valuable inputs. 

I have verified that I have Sun Java 6 and Browser Plugin installed. Also, apart from Sun Java, I do not have any other version of Java installed (like Open JDK).

Once I installed the ubuntu-restricted-extras package, it initially seemed to me that the issue was resolved. However, when I restarted the system, I get the same error (mentioned below).

summary of the issue:

1. Applets were working in some of the cases.
2. However, the website (ttp://www.indiabulls.com/equities/techanalysis/tech_analysis.asp) - is giving trouble. Below is the error that I get. Please note, that the applet worked once when I installed the ubuntu-restricted-extras package. But for some reason, the issue is back (in less than 10 mins, when I restarted the system)

*******************************************************************************
java.lang.NullPointerException
	at equis.metastock.MS4Java.repaint(ms4java.java:1154)
	at sun.awt.X11.XCanvasPeer.setBackground(XCanvasPeer.java:112)
	at sun.awt.X11.XPanelPeer.setBackground(XPanelPeer.java:79)
	at java.awt.Component.setBackground(Component.java:1578)
	at equis.metastock.MS4Java.init(ms4java.java:878)
	at sun.applet.AppletPanel.run(AppletPanel.java:425)
	at java.lang.Thread.run(Thread.java:619)
********************************************************************************

Please help. Thanks again for the assistance. 

Regards,

Anoop.

---

### Post by agraano on 2008-08-27
Hello, 

Please help me with the Java installation issue. 

Thank you.
AA

---

### Post by aloshbennett on 2008-08-28
Test: Does the applets load from here
[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

---

### Post by agraano on 2008-08-28
Hi aloshbennett,

The Java Applet works when I go to the link that you provided.

In several cases, the Java Applet does work. However, it doesn't seems to work for [www.indiabulls.com/equities/techanalysis/tech_analysis.asp](www.indiabulls.com/equities/techanalysis/tech_analysis.asp)

Can you please try the above link and check if the applet is working for you?

Regards,

Anoop.

---

### Post by aloshbennett on 2008-08-28
I checked once sometime and my firefox froze. Looks like its pretty huge in size. Let me check tonight.

---

### Post by agraano on 2008-08-28
Thanks for looking to this. Just as an info, the website is a charting tool (stock price trending). And it worked [once] in Opera. But was short lived.

Please let me know once you find out anything. FYI - This applet works fine in Windows XP.

Anoop

---

### Post by Thelasko on 2008-08-28
> **oooh said:**
> Same problem here. However, I can properly see youtube, but can not use the JAVA applications in facebook.

I have installed:
sun-java6-jre 
and all dependancies

I dont find sun-java6-plugin in the repositories

JRE is installed, but not listed in about:plugins in firefox.

By the way , I am using Sony Vaio 64bits

Because your using 64-bit, your problem is very different than the OP's.  Please look on the [64-bit section]("http://ubuntuforums.org/forumdisplay.php?f=343"), and if you have a question, post it there.

---

### Post by silverglade00 on 2008-08-28
Using View Source for that page, I found this:

```
<applet align="baseline" code="equis.metastock.MS4Java.class"  codebase="http://www.indiabulls.com/" height="400" id="Applet1" name="MS4Java" width="700" archive="equis/metastock/ms4java.jar" VIEWASTEXT>
                              <param NAME="ad" VALUE="false">

```

I believe that MSJava part is the problem here. Probably not real Java, but J# or J++ or some funky thing. It won't load for me either. Also, when I loaded the clock page from aloshbennett, only the top clocks loaded, the bottom did not. Hope that helps!

---

### Post by philinux on 2008-08-28
> **silverglade00 said:**
>  It won't load for me either. Also, when I loaded the clock page from aloshbennett, only the top clocks loaded, the bottom did not. Hope that helps!

Yep same here. If I try a different plugin I can get all the clocks to load but then cant load this.
[thinkbroadband]("http://www.thinkbroadband.com/speedtest.html") 

So I reverted to the icedtea gcj plugin as I use that speedtester a lot.

---

### Post by aloshbennett on 2008-08-28
I dont think so. Its a normal java class called MS4Java. Maybe MS would be metastock.
Maybe OP could download [http://www.indiabulls.com/equis/metastock/ms4java.jar](http://www.indiabulls.com/equis/metastock/ms4java.jar) and see.

Another problem could be that, the class is loaded of a jar. Though it shouldnt be a problem, it is not commonnly used.

---

### Post by agraano on 2008-08-28
> **aloshbennett said:**
> I dont think so. Its a normal java class called MS4Java. Maybe MS would be metastock.
Maybe OP could download [http://www.indiabulls.com/equis/metastock/ms4java.jar](http://www.indiabulls.com/equis/metastock/ms4java.jar) and see.

Another problem could be that, the class is loaded of a jar. Though it shouldnt be a problem, it is not commonnly used.

Hi,

Since the applet did not loaded for other users too, I think, the real issue would be to understand,

a) If there is a issue with the way the website / applet in question has been designed. (However, please note that the applet loaded once in Opera.)
b) If there is a issue with the the way linux handles .Jar files.
c) Do you think, there is a workaround for this problem? - I downloaded the .Jar file. But what is the next step?

Regards,
Anoop.

---

### Post by agraano on 2008-08-29
> **agraano said:**
> Hi,

Since the applet did not loaded for other users too, I think, the real issue would be to understand,

a) If there is a issue with the way the website / applet in question has been designed. (However, please note that the applet loaded once in Opera.)
b) If there is a issue with the the way linux handles .Jar files.
c) Do you think, there is a workaround for this problem? - I downloaded the .Jar file. But what is the next step?

Regards,
Anoop.

Hi All,

Need your input to the above issue. I am kind of under the assumption that perhaps, its an issue with the particular website / applet in question. 

Yes, I do not control / own the website, but I do use it for technical charting. For all practical purposes, I am using Windows XP, which do not give me any trouble with the above applet. But the question is, if the the applet is a Java feature - they why it doesn't function in Linux but works fine with Windows.

If its a design flaw by the creators, then are there any guesses as to why they might have erred? Examples could be (might be a stupid one - I am novice to linux) the classes in the Jar file is looking for the temp folder path (c:\Document Settings\ user\ temp\ folder, but this doesn't exist in linux ? 

But there need to exist a reason as to where is the flaw. Can any one help please. I can at least try to contact the company (website) with some specific information and ask them to fix it. 

Regards,

Anoop Agrawal.

---

### Post by wolfie2x on 2008-08-29
some java applets just wont work with some java versions.

for example facebook applet doesn't work with SunJava6 on firefox..
[http://ubuntuforums.org/showthread.php?t=870884&highlight=java6+firefox]("http://ubuntuforums.org/showthread.php?t=870884&highlight=java6+firefox")

---

### Post by Thelasko on 2008-08-29
> **wolfie2x said:**
> for example facebook applet doesn't work with SunJava6 on firefox..
[http://ubuntuforums.org/showthread.php?t=870884&highlight=java6+firefox]("http://ubuntuforums.org/showthread.php?t=870884&highlight=java6+firefox")

That thing won't work anywhere (except windows).  Who coded that thing?

---

### Post by Crafty Kisses on 2008-08-29
Yeah the Java application worked, could be a number of issue, post the results of this command:```
glxinfo
``` I also would like to know the output of this command:```
java --version
```
Thanks!

---

### Post by agraano on 2008-08-29
> **Codename said:**
> Yeah the Java application worked, could be a number of issue, post the results of this command:```
glxinfo
``` I also would like to know the output of this command:```
java --version
```
Thanks!

Hi Codename, below is the result of both the commands.

```
anoop@anoop-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

```

anoop@anoop-desktop:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)
```

---

