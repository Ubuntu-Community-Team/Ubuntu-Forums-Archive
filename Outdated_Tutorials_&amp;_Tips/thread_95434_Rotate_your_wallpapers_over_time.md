---
title: "Rotate your wallpapers over time"
date: 2005-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by thechitowncubs on 2005-11-26
This program was custom made for me by a developer in the nautilus channel. Thanks gicmo!

change-bg rotates your wallpaper (jpg/png) in a gnome enviornment over a specified amount of time. 

[B]
[https://wiki.ubuntu.com/RotateWallpapers](https://wiki.ubuntu.com/RotateWallpapers)[/B]

---

### Post by Zerocool10482 on 2006-02-25
How do I use this thing? I'm a newbie and I just wanted to have my wallpaper to change over time. I tried using it. Can you give me a HOWTO?

---

### Post by stalefries on 2006-02-25
```
./change-bg <seconds> <location of wallpapers>
``` 
You type that, replacing <seconds> with the amount of seconds between wallpaper switches, then replace <location of wallpapers> with the paths to all of your wallpapers. It's not too hard.

Scratch that. I just got a boat-load of errors.

```
Package gnome-vfs-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnome-vfs-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnome-vfs-2.0' found
change-bg.c:26:35: error: libgnomevfs/gnome-vfs.h: No such file or directory
change-bg.c:27:32: error: gconf/gconf-client.h: No such file or directory
change-bg.c:28:18: error: glib.h: No such file or directory
change-bg.c:32: error: syntax error before &#8216;*&#8217; token
change-bg.c:32: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gcc&#8217;
change-bg.c:32: warning: data definition has no type or storage class
change-bg.c:34: error: syntax error before &#8216;*&#8217; token
change-bg.c:34: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;uri&#8217;
change-bg.c:34: warning: data definition has no type or storage class
change-bg.c:35: error: syntax error before &#8216;*&#8217; token
change-bg.c:35: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;files&#8217;
change-bg.c:35: warning: data definition has no type or storage class
change-bg.c:36: error: syntax error before &#8216;*&#8217; token
change-bg.c:36: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;iter&#8217;
change-bg.c:36: warning: data definition has no type or storage class
change-bg.c:38: error: syntax error before &#8216;change_picture&#8217;
change-bg.c:38: error: syntax error before &#8216;data&#8217;
change-bg.c:39: warning: return type defaults to &#8216;int&#8217;
change-bg.c: In function &#8216;change_picture&#8217;:
change-bg.c:40: error: &#8216;GnomeVFSURI&#8217; undeclared (first use in this function)
change-bg.c:40: error: (Each undeclared identifier is reported only once
change-bg.c:40: error: for each function it appears in.)
change-bg.c:40: error: &#8216;nuri&#8217; undeclared (first use in this function)
change-bg.c:41: error: &#8216;gboolean&#8217; undeclared (first use in this function)
change-bg.c:41: error: syntax error before &#8216;result&#8217;
change-bg.c:45: warning: implicit declaration of function &#8216;gconf_client_get_default&#8217;
change-bg.c:45: warning: assignment makes pointer from integer without a cast
change-bg.c:47: error: request for member &#8216;data&#8217; in something not a structure or union
change-bg.c:48: warning: implicit declaration of function &#8216;gnome_vfs_uri_append_string&#8217;
change-bg.c:50: warning: implicit declaration of function &#8216;gnome_vfs_uri_to_string&#8217;
change-bg.c:50: error: &#8216;GNOME_VFS_URI_HIDE_USER_NAME&#8217; undeclared (first use in this function)
change-bg.c:51: error: &#8216;GNOME_VFS_URI_HIDE_PASSWORD&#8217; undeclared (first use in this function)
change-bg.c:52: error: &#8216;GNOME_VFS_URI_HIDE_TOPLEVEL_METHOD&#8217; undeclared (first use in this function)
change-bg.c:53: error: &#8216;GNOME_VFS_URI_HIDE_FRAGMENT_IDENTIFIER&#8217; undeclared (first use in this function)
change-bg.c:54: error: &#8216;GNOME_VFS_URI_HIDE_HOST_PORT&#8217; undeclared (first use in this function)
change-bg.c:55: error: &#8216;GNOME_VFS_URI_HIDE_HOST_NAME&#8217; undeclared (first use in this function)
change-bg.c:55: warning: assignment makes pointer from integer without a cast
change-bg.c:59: error: &#8216;result&#8217; undeclared (first use in this function)
change-bg.c:59: warning: implicit declaration of function &#8216;gconf_client_set_string&#8217;
change-bg.c:64: warning: implicit declaration of function &#8216;g_free&#8217;
change-bg.c:66: error: &#8216;FALSE&#8217; undeclared (first use in this function)
change-bg.c:70: error: request for member &#8216;next&#8217; in something not a structure or union
change-bg.c:71: error: request for member &#8216;next&#8217; in something not a structure or union
change-bg.c:76: error: &#8216;TRUE&#8217; undeclared (first use in this function)
change-bg.c:77: warning: control reaches end of non-void function
change-bg.c: At top level:
change-bg.c:80: error: syntax error before &#8216;visit_files&#8217;
change-bg.c:80: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;gchar&#8217;
change-bg.c:80: error: syntax error before &#8216;*&#8217; token
change-bg.c:85: warning: return type defaults to &#8216;int&#8217;
change-bg.c: In function &#8216;visit_files&#8217;:
change-bg.c:86: error: &#8216;GList&#8217; undeclared (first use in this function)
change-bg.c:86: error: syntax error before &#8216;)&#8217; token
change-bg.c:87: error: &#8216;recurse&#8217; undeclared (first use in this function)
change-bg.c:87: error: &#8216;TRUE&#8217; undeclared (first use in this function)
change-bg.c:89: error: &#8216;info&#8217; undeclared (first use in this function)
change-bg.c:89: error: &#8216;GNOME_VFS_FILE_INFO_FIELDS_MIME_TYPE&#8217; undeclared (first use in this function)
change-bg.c:90: warning: implicit declaration of function &#8216;g_str_equal&#8217;
change-bg.c:93: warning: implicit declaration of function &#8216;g_list_prepend&#8217;
change-bg.c:93: warning: implicit declaration of function &#8216;g_strdup&#8217;
change-bg.c:93: error: &#8216;rel_path&#8217; undeclared (first use in this function)
change-bg.c:97: error: &#8216;recursing_will_loop&#8217; undeclared (first use in this function)
change-bg.c:98: warning: control reaches end of non-void function
change-bg.c: In function &#8216;main&#8217;:
change-bg.c:103: error: &#8216;GnomeVFSResult&#8217; undeclared (first use in this function)change-bg.c:103: error: syntax error before &#8216;result&#8217;
change-bg.c:104: error: &#8216;GMainLoop&#8217; undeclared (first use in this function)
change-bg.c:104: error: &#8216;ml&#8217; undeclared (first use in this function)
change-bg.c:112: warning: implicit declaration of function &#8216;gnome_vfs_init&#8217;
change-bg.c:117: warning: implicit declaration of function &#8216;gnome_vfs_make_uri_from_shell_arg&#8217;
change-bg.c:117: warning: assignment makes pointer from integer without a cast
change-bg.c:128: error: &#8216;result&#8217; undeclared (first use in this function)
change-bg.c:128: warning: implicit declaration of function &#8216;gnome_vfs_directory_visit&#8217;
change-bg.c:129: error: &#8216;GNOME_VFS_FILE_INFO_GET_MIME_TYPE&#8217; undeclared (first use in this function)
change-bg.c:130: error: &#8216;GNOME_VFS_FILE_INFO_FORCE_FAST_MIME_TYPE&#8217; undeclared (first use in this function)
change-bg.c:131: error: &#8216;GNOME_VFS_DIRECTORY_VISIT_LOOPCHECK&#8217; undeclared (first use in this function)
change-bg.c:132: error: &#8216;GNOME_VFS_DIRECTORY_VISIT_SAMEFS&#8217; undeclared (first use in this function)
change-bg.c:136: error: &#8216;GNOME_VFS_OK&#8217; undeclared (first use in this function)
change-bg.c:138: warning: implicit declaration of function &#8216;gnome_vfs_result_to_string&#8217;
change-bg.c:138: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;int&#8217;
change-bg.c:142: warning: implicit declaration of function &#8216;gnome_vfs_uri_new&#8217;
change-bg.c:142: warning: assignment makes pointer from integer without a cast
change-bg.c:146: warning: implicit declaration of function &#8216;g_timeout_add&#8217;
change-bg.c:148: warning: implicit declaration of function &#8216;g_main_loop_new&#8217;
change-bg.c:148: error: &#8216;FALSE&#8217; undeclared (first use in this function)
change-bg.c:151: warning: implicit declaration of function &#8216;g_main_loop_run&#8217;

```

---

### Post by JoshHendo on 2006-02-25
Works fine for me :D.
I will post a full (noob friendly) how to on my blog soon :)

-edit-

Here is a link for those looking for a full tutorial :)
[http://ubuntuos.com/2006/02/howto-rotate-your-wallpapers-over-time-gnome.html](http://ubuntuos.com/2006/02/howto-rotate-your-wallpapers-over-time-gnome.html)

---

### Post by stalefries on 2006-02-25
Worked! I missed that part of the dependencies. By the way, would it be possible to add this to some start-up script or other?

---

### Post by bicchi on 2006-02-25
[QUOTE=stalefries]Worked! I missed that part of the dependencies. By the way, would it be possible to add this to some start-up script or other?[/QUOTE]

Follow the menu: System -> Preferences -> Sessions 
[Startup Programs] [Add] . . . . .

---

### Post by i3dmaster on 2006-02-25
very nice! good job man!

---

### Post by ShiftyPowers on 2006-04-09
anyone know an easy way to have this start everytime a gnome session starts?  I have it working, which is awesome, but it would be really cool to not have to start terminal every time.

---

### Post by sYs^ on 2006-04-10
[QUOTE=ShiftyPowers]anyone know an easy way to have this start everytime a gnome session starts?  I have it working, which is awesome, but it would be really cool to not have to start terminal every time.[/QUOTE]

Man, just read the comments:

[QUOTE=bicchi]Follow the menu: System -> Preferences -> Sessions
[Startup Programs] [Add] . . . . .[/QUOTE]

---

### Post by worty on 2006-04-10
I haven't tested this specific prog but there's another one out there that I use called Wallpaper Tray that works pretty well too.

---

### Post by lotu5 on 2006-05-09
this is cool, but for large wallpapers it can be a bit jarring. what would be really awesome would be to implement the kind of fading that mac os x does between desktops... 

since this program just tells gnome what to do, it seems like that feature would have to go into the gnome desktop program itself. it looks like gnome pixbufs do have alpha values though, so it shoudl be possible...

---

