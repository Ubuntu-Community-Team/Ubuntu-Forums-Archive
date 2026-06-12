---
title: "Force all applications to open maximized?"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by NonStop on 2012-10-25
Is there any way to force all applications to open fully maximized? 

I'm finding lots of my applications are opening non-maxmized like below - see the top-right hand corner - the maximized option is still available - and at the bottom of the window you can see the gap between the app and the taskbar:

[http://imageshack.us/a/img338/448/201210252147421440x900s.png](http://imageshack.us/a/img338/448/201210252147421440x900s.png)

Thanks in advance people.

---

### Post by NonStop on 2012-10-29
Anyone?

---

### Post by juancarlospaco on 2012-10-29
There was a package for netbook edition named Maximus, that do it, just a Lib, no gui, no cli, it just maximize, i dunno the actual state.

---

### Post by amjjawad on 2012-10-31
> **NonStop said:**
> Is there any way to force all applications to open fully maximized? 

I'm finding lots of my applications are opening non-maxmized like below - see the top-right hand corner - the maximized option is still available - and at the bottom of the window you can see the gap between the app and the taskbar:

[http://imageshack.us/a/img338/448/201210252147421440x900s.png](http://imageshack.us/a/img338/448/201210252147421440x900s.png)

Thanks in advance people.

Hi there,

I'm sorry, it is a bit confusing. I'd appreciate if you explain what exactly are you looking for?

You want all your applications to start with Maximized window? or you don't want that?

I'm running Lubuntu 12.04 64bit on Lenovo Core i5 2nd generation and 4GB RAM.

PCManFM remembers it was fully maximized the last time so when I re-open it later, it is fully maximized.
Some other applications are not meant to be fully maximized, like Openbox Configuration Manager which seem it can't remember how I maximized it the previous time I opened it.

---

### Post by NonStop on 2012-11-07
> **amjjawad said:**
> Hi there,

I'm sorry, it is a bit confusing. I'd appreciate if you explain what exactly are you looking for?

You want all your applications to start with Maximized window? or you don't want that?

I'm running Lubuntu 12.04 64bit on Lenovo Core i5 2nd generation and 4GB RAM.

PCManFM remembers it was fully maximized the last time so when I re-open it later, it is fully maximized.
Some other applications are not meant to be fully maximized, like Openbox Configuration Manager which seem it can't remember how I maximized it the previous time I opened it.

I want all my applications to start with maximized window, yes.

Currently, PCManFM doesn't open fully maximized, it opens like the picture in the original post :(

---

### Post by urukrama on 2012-11-07
Add the following to the <applications> section in your rc.xml (in /home/USERNAME/.config/openbox/):

```
 <application class="*">
      <maximized>yes</maximized>
    </application>
```

If you also want no window decorations, use the following:

```
 <application class="*">
      <decor>no</decor>
      <maximized>yes</maximized>
    </application>
```

or 

```
 <application class="*">
      <fullscreen>yes</fullscreen>
    </application>
```


For more information: [http://openbox.org/wiki/Help:Applications](http://openbox.org/wiki/Help:Applications)

---

### Post by amjjawad on 2012-11-08
> **NonStop said:**
> Currently, PCManFM doesn't open fully maximized, it opens like the picture in the original post :(

[IMG]http://imageshack.us/a/img338/448/201210252147421440x900s.png[/IMG]

I just got my new glasses :D and as far as I can see, it IS fully maximized unless I really miss something here :(

---

### Post by NonStop on 2012-11-08
> **urukrama said:**
> Add the following to the <applications> section in your rc.xml (in /home/USERNAME/.config/openbox/):

```
 <application class="*">
      <maximized>yes</maximized>
    </application>
```

If you also want no window decorations, use the following:

```
 <application class="*">
      <decor>no</decor>
      <maximized>yes</maximized>
    </application>
```

or 

```
 <application class="*">
      <fullscreen>yes</fullscreen>
    </application>
```


For more information: [http://openbox.org/wiki/Help:Applications](http://openbox.org/wiki/Help:Applications)


Thank you, what exactly should I do, bit of a lubunut newbie, where should I go and what should I do. I'm pariculary interested in PCManFM opening maximised.

> **amjjawad said:**
> [IMG]http://imageshack.us/a/img338/448/201210252147421440x900s.png[/IMG]

I just got my new glasses :D and as far as I can see, it IS fully maximized unless I really miss something here :(

Thanks for the reponse, top left, middle box has one box showing, which indicates it needs to be clicked to be fully maximised. There are two boxes overlpapping each other when fully maximised.

---

### Post by amjjawad on 2012-11-08
> **NonStop said:**
> Thanks for the reponse, top left, middle box has one box showing, which indicates it needs to be clicked to be fully maximised. There are two boxes overlpapping each other when fully maximised.

Forget about the icon and how does it look like.
Have a look at the window of your PCManFM. If the window is covering the whole screen then it **IS** fully maximized.

---

### Post by NonStop on 2012-11-08
> **amjjawad said:**
> Forget about the icon and how does it look like.
Have a look at the window of your PCManFM. If the window is covering the whole screen then it **IS** fully maximized.

It isn't fully maximisd, because if I put my mouse on the far top right hand corner, the close button isn't highighted, instead the move window cursor pops up.

---

### Post by urukrama on 2012-11-09
> **NonStop said:**
> Thank you, what exactly should I do, bit of a lubunut newbie, where should I go and what should I do. I'm pariculary interested in PCManFM opening maximised.

In your home directory (/home/ian) there is a hidden directory called .config (press Ctrl+H) to see those. In that there is a directory called openbox, and in that are several files that control Openbox' behaviour (Openbox is the window manager in Lubuntu).

The file you need to edit is the rc.xml, which is the configuration file for Openbox. Towards the end of that file, there is a section that begins as follows:

```
  <applications>
    <!--
  # this is an example with comments through out. use these to make your
  # own rules, but without the comments of course.

  <application name="first element of window's WM_CLASS property (see xprop)"
              class="second element of window's WM_CLASS property (see xprop)"
               role="the window's WM_WINDOW_ROLE property (see xprop)">
  # the name or the class can be set, or both. this is used to match
  # windows when they appear. role can optionally be set as well, to
  # further restrict your matches.

  # the name, class, and role use simple wildcard matching such as those
  # used by a shell. you can use * to match any characters and ? to match
  # any single character.

  # when multiple rules match a window, they will all be applied, in the
  # order that they appear in this list


    # each element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>yes</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not

    <position>
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      <x>center</x>
      # a number like 50, or 'center' to center on screen
      <y>200</y>
      # a number like 50, or 'center' to center on screen
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>

    <focus>yes</focus>
    # if the window should try be given focus when it appears. if this is set
    # to yes it doesn't guarantee the window will be given focus. some
    # restrictions may apply, but Openbox will try to

    <desktop>1</desktop>
    # 1 is the first desktop, 'all' for all desktops

    <layer>normal</layer>
    # 'above', 'normal', or 'below'

    <iconic>no</iconic>
    # make the window iconified when it appears, or not

    <skip_pager>no</skip_pager>
    # asks to not be shown in pagers

    <skip_taskbar>no</skip_taskbar>
    # asks to not be shown in taskbars. window cycling actions will also
    # skip past such windows

    <fullscreen>yes</fullscreen>
    # make the window in fullscreen mode when it appears

    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no)
  </application>

  # end of the example
-->
```

Post the code I gave you earlier right after that. When you reconfigure Openbox (using the standard menu entry, or type *openbox --reconfigure* in a terminal), and every application you launch should be automatically maximized. Whatever applications you already had running while you reconfigured Openbox will have to be restarted to be automatically maiximized.

---

