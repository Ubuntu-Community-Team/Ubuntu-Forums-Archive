---
title: "[HOWTO] Devilspie on AMD64 - My personal little work...."
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by MiddleBrooker on 2005-03-28
Hi,
I've tried to run the beautiful Devilspie program on my AMD64 Shuttle XPC, so with the default Ubuntu package installed through the classis Ubuntu repository I've got thi error message:

```

mbrooker@Ubushut:~$ devilspie
devilspie: relocation error: devilspie: undefined symbol: _wnck_atom_get

```

This happend when I try to lauch any terminal by the Devilspie manipulation.

So after that I've tried to compile the source code by the Official Website:
[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

The first error after "make" was this:

```

devilspie-action-resize.gob: In function `___1_devilspie_action_resize_run':
devilspie-action-resize.gob:75: error: too few arguments to function `wnck_window_unminimize'
make[2]: *** [devilspie-action-resize.o] Error 1

```

This happen due some changes on the libwnck libraries and can be fixed by an edit of the file devilspie-action-resize.gob under 'src' direcotry :

```

   override (DevilsPie:Action) gboolean run(DevilsPie:Action *self (check null type), Wnck:Window *window (check null type)) {
     DevilsPieActionResize *a = (DevilsPieActionResize*)self;
**-    guint32 timestamp;    /* ADD THIS LINE */ **
     /* Assume that a true/false tristate in a boolean context is correct */
     /* Assume the user is not totally stupid and has not set both
     maximize and minimize */
     if (a->minimized == TRI_TRUE)
       wnck_window_minimize(window);
     else if (a->minimized == TRI_FALSE)
-      wnck_window_unminimize(window, timestamp);
**+      wnck_window_unminimize(window);   /* NOW INSERT THE PREVIOUS DECLARED VARIABLE AND REMOVE THIS LINE  ** 
     /* Handle full screen */
     if (a->fullscreen != TRI_UNSET) {
         g_print("fullscreen\n");

```

Simple modification that don't make me able to compile the source code, because now I've got another error:

```

collect2: ld returned 1 exit status
make[2]: *** [devilspie] Error 1

```

And at this point I'll be very happy if somebody can explane to me where is the error  :?: 
Becasue I'm not be able to understand it!


OK, after this I've decided to make Devilspie works on my AMD64 Shuttle XPC by adding this custom repositories to my /etc/apt/sources.list :

```

deb http://debian-amd64.alioth.debian.org/pure64 sid main
deb-src http://debian-amd64.alioth.debian.org/pure64 sid main
deb-src http://ftp.debian.org/debian/ unstable main

```

and after that:

```

apt-get install devilspie

```

So agree to the unauthenticated packages :

```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libwnck4
The following NEW packages will be installed:
  devilspie libwnck4
0 upgraded, 2 newly installed, 0 to remove and 379 not upgraded.
Need to get 136kB of archives.
After unpacking 492kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  libwnck4 devilspie
Install these packages without verification [y/N]?

```

OK! This is an extreme method that cannot be use, but now my Devilspie work perfectly on my machine!

I hope to be helpful for somebody by posting my .devilspie.xml code too  :mrgreen: 

```

<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="Desktop Terminal"/>
      </matcher>
    </matchers>
    <actions>
      <!-- Display on all workspaces -->
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
      <!-- Set the window type. DOCK seems to give us the right properties and stacking order -->
      <action name="DevilsPieActionSetWintype">
        <property name="wintype" value="DOCK"/>
      </action>
      <!-- Don't want to be above normal windows, just the desktop -->
      <action name="DevilsPieActionLayer">
        <property name="above" value="FALSE"/>
      </action>
      <!-- Remove from window lists (e.g. alt-tab, panel window list, etc) -->
      <action name="DevilsPieActionHide">
        <property name="skip_pager" value="TRUE"/>
        <property name="skip_tasklist" value="TRUE"/>
      </action>
      <!-- Should be obvious :) -->
      <action name="DevilsPieActionSetGeometry">
        <property name="width" value="1024"/>
        <property name="height" value="768"/>
        <property name="yoffset" value="575"/>
      </action>
    </actions>
  </flurb>
</devilspie>

```

Best Regards to ALL!
MiddleBrooker

---

