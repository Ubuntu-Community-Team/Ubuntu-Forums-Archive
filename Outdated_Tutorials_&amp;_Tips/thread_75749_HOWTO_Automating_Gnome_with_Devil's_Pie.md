---
title: "HOWTO: Automating Gnome with Devil's Pie"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Wolki on 2005-10-14
Disclaimer: This is quite long, I'm sorry, but I tried to be detailed. I'm open for all suggestions and criticisms and would be happy to hear them. Thank you.

Note: This howto is intended for Devil's Pie 0.10, the one included with breezy. I do not know whether it will work with older versions, and the newest use a different method for configuration. A short introduction to the new format follows at the end.

**Introduction**

Gnome is a desktop environment that is - in my opinion - quite pleasant to use. But sometimes a user hits the limits of what is possible with plain Gnome. For example, a user who has developed a setup of applications on workspaces has to move the windows manually; there is no way to tell standard Gnome to - for example - always open Evolution on the second workspace, or Firefox always maximized, to have Gaim converstaions on all workspaces, to fix applications that always start in the wrong position and too small a window, and so on.
Users who want such functionality need not worry, it is possible to add this - and much , much more - with a little, but powerful application called Devil's Pie. The problem is that its configuration is quite technical and can be confusing. I will try to make this a little more transparent.

[SIZE="4"]Part I: The Basics[/SIZE]

**Installation**

Installation of Devil's Pie is quite easy; you can just use synaptic. Make sure you have universe enabled ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)). If you want to do it from a command line, "sudo apt-get install devilspie".
After installation, you will probably want to add it to your autostart. Open System -> Preferences -> Session, go to the startup programs tab, Add. Enter "devilspie" into the command field, and set the order to something low. 
Devil's Pie by default reads its configuration from a hidden file called .devilspie.xml that you have to create. Open gEdit (or your favorite other text editor) and save a new document as ".devilspie.xml". 

[B]
Basic setup of the configuration file[/B]

Now, lets start populating the configuration file. It is in XML so it might look confusing, especially to people not used to programming or XML. You'll get used to it, it looks by far harder than it is.
Devil's Pie uses a set of rules (called "flurbs"... I didn't name it, don't blame me :)) to determine what it should do with windows. If there is no rule for a window, it will do nothing, so if you have no flurbs it will just behave like normal gnome. The Structure is like this:

```

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
<!-- replace this lines with your flurbs -->
</devilspie>

```

So start by pasting this in your (still empty) configuration file.

**Flurbs**

OK, now it's time to talk in more details about flurbs. Like I already said, flurbs are rules. At the beginning I gave the example of automatically moving Evolution to your second workspace. How to formulate this as a rule? "If a window is called Evolution -> Move it to Workspace number two". A little more abstract: "If a window fits (criteria) -> Do (actions)". And finally, in a way that Devil's Pie can understand:

```

<flurb>
    <matchers>
        <!-- replace this with your criteria -->
    </matchers>
    <actions>
        <!-- replace this with your actions -->
    </actions>
</flurb>

```

Note especially that you can have several of each in one flurb: For example, its possible to not only move Evolution to Workspace 2, but also maximize it at the same time. 
Let's continue to implement moving Evolution as a flurb.

**Matchers**

Explaining matchers in more detail is something I'd like to hold for later, As for a good explanation I'd have to go into some details. For our example, I just give you a ready-made matcher and you'll understand later how it works exactly.

```

<matcher name="DevilsPieMatcherWindowName">
    <property name="window-title" value="Evolution"/>
</matcher>

```

**Actions**

Now, Devil's Pie is quite powerful and can do a lot. Again, I'll give you a reference and some more details later. This action moves Evolution:

<action name="DevilsPieActionSetWorkspace">
    <property name="workspace_index" value="2"/>
</action>

**Putting it together**

How does this look like when it's put together? Try it.

If you've understood the structure so far, you should arrive somewhere near this:

```

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="evolution"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="workspace_index" value="2"/>
      </action>
    </actions>
  </flurb>
</devilspie>

```

If your version is different, take another look to see if you understand how i arrived at this. If you still don't, send me angry PMs that my Howtos are too hard to understand :) (oh and include what and why you didn't understand it so that I can try to fix that^^;; ).

Let's get away from dry theory for a bit and try it out! Save the above as your .devilspie.xml, (re)start Devil's Pie. and start Evolution. It should now open on your second workspace :)

Note that after editing the configuration file, devilspie needs to be restarted for the changes to take effect if it's already running, so "killall devilspie" followed by "devilspie &" will make sure that you're using the new version.

If you managed to get this far, give yourself a pat on the back and celebrate a little. You've taken the first step to become a Devil's Pie master. Continue reading when you feel up for the next step.

[SIZE="4"]Part 2: More on Matchers[/SIZE]

As promised, here's more about Matchers. Let's start with another example.
With Hoary, a lot of users complained that they were missing IMs, because gaim did not sufficiently alert them that they got a message. In Breezy, the application glows in the task list if it wants to alert the user. But what if you're on another workspace? Unless you have a global task bar, you won't see the notification. The solution is of course to make your conversation window sticky on all desktops. Let's see if we can get Devil's Pie to do that for us.

We're covering more on actions later, here's what we need for this flurb:
```

    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
    </actions>

```

Time to look at the matcher part of our flurb. As we've seen, it starts with <matchers> and ends with </matchers>. Our last flurb then had a line "<matcher name="DevilsPieMatcherWindowName">" This tells Devil's Pie which matcher to use.
There are two you can choose here: DevilsPieMatcherWindowName, which we've already seen in action, and DevilsPieMatcherAlways.

**DevilsPieMatcherAlways**

This one simply matches every window :) Thus it doesn't need any further arguments; If you want to match all windows the following is a complete matchers part:
```
<matchers>
     <matcher name="DevilsPieMatcherAlways"/>
</matchers>
```

Since DevilsPieMatcherAlways does not have any properties you do not need to close it by a seperate tag, but can instead add a slash before the end of the tag. The above is equivalent to 
```
<matchers>
     <matcher name="DevilsPieMatcherAlways">
     </matcher>
</matchers>
```
I will occasionally use this shorter notation in this guide, but you can also keep the longer version.


**DevilsPieMatcherWindowName**

This is a bit more interesting. This will allow us to match windows based on more specific criteria. Of course, this means we have to tell Devil's Pie what these criteria are :) In our first example, we did this with the line "<property name="application_name" value="Evolution"/>". This is a structure we will see again later; we specify a property and a value for that property. For DevilsPieMatcherWindowName, we have 3 different properties we can use: window-title, application-name and window-role. window-title and application-name explain themselves, one matches the window title (what you see in the title-bar), the other the application name. window-role is more hard to explain, and not all windows have this property. It's what role a window fills, if that makes sense.

What values can we pass to these properties? If you know about "regular expressions", good for you, you can use regexps. If not, explaining them would by far break the limits of this (much too long) Howto. A simple version: If you set "xyz", the matcher will accept everything that contains "xyz". So, caution: if you match "gaim" by window_title, this will also accept other windows that contain "gaim" in their name, like firefox on certain websites.

So, this would match all Gaim windows: 
```

<matchers>
  <matcher name="DevilsPieMatcherWindowName">
    <property name="application_name" value="gaim"/>
  </matcher>
</matchers>

```

We're not done yet, this would also apply to the buddy list window, and we only want to pin the conversations. Gaim is nice and sets window roles; IM windows have the role "conversation". So this is the .devilspie.xml that contains our first flurb and a solution for our current example:

```

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="Evolution"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="workspace_index" value="2"/>
      </action>
    </actions>
  </flurb>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="gaim"/>
        <property name="window_role" value="conversation"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
    </actions>
  </flurb>
</devilspie>

```

**Finding the right values**

I didn't tell you yet how to find out what window_title, application_name and window_role a certain window has. This can be a bit messy, as some applications don't play nice here.
It's easy for window_title, since you can just read that in the title bar. Now for the other two...
First a way that often works: Execute ```
xprop | egrep "(WM_WINDOW_ROLE)|(WM_CLASS)"
``` in a terminal. Your mouse pointer will become a crosshair. Click on a window you want to know more about, and you will get an output like:

WM_WINDOW_ROLE(STRING) = "conversation"
WM_CLASS(STRING) = "gaim", "Gaim"

The WM_WINDOW_ROLE(STRING) specified here is the window_role for Devil's Pie; if it doesn't output that line the window does not have a window_role. The first part of the WM_CLASS(STRING) line (in this case "gaim") is sometimes, but by far not always the application_name. Some exceptions are, for example, gnome-terminal and nautilus. Sometimes you can guess the right application_name, sometimes not.
The definitive way to find out the application name is enabling the debug flurb and starting Devil's Pie from the command line, it will tell you the window-title, application-name and window-role of each existing window and each new one you open. Save the following as ".devilspie-debug.xml".
```

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb name="Print Window Names">
    <matchers>
      <matcher name="DevilsPieMatcherAlways"/>
    </matchers>
    <actions>
      <action name="DevilsPieActionDebug"/>
    </actions>
  </flurb>
</devilspie>

```
Start devilspie with "devilspie .devilspie-debug.xml". It will output the relevant information for all windows, close it with <ctrl>-<c> afterwards. You should then be able to find out (sometimes with a little creativity ^^;; ) how to match those windows. (If there's a better way to find out the application_name, please tell me and I'll update this).

(Hint: gnome-terminal sets it's window_role as "gnome-terminal-<lots of confusing numbers>", so match window_role against "gnome-terminal" to get all gnome-terminal windows)

OK, that's enough (I hope) about one side of the rules, next let's look at the cool things we can do on the other side.

[SIZE="4"]Part 3: Actions[/SIZE]

Taking one of the examples, we see that the actions Part looks quite similar to the matchers.

```

<actions>
   <action name="DevilsPieActionSetWorkspace">
     <property name="pinned" value="TRUE"/>
   </action>
</actions>

```

Again, we choose something, then set values to it's properties. If you want to set the "abc" property of a action type "zyx" to "uvw", you do it like this:

```

<actions>
   <action name="zyx">
     <property name="abc" value="uvw"/>
   </action>
</actions>

```

Here's a list of action types:  DevilsPieActionHide, DevilsPieActionDecorate, DevilsPieActionLayer, DevilsPieActionSaveGeometry, DevilsPieActionSetGeometry, DevilsPieActionSetWorkspace, DevilsPieActionResize, DevilsPieActionDebug, DevilsPieActionSetWintype, and DevilsPieActionOpacity.

Remember: you only have to set Actions if you actually want to change something, otherwise just leave them out.

**DevilsPieActionHide** is for hiding windows from the task list or the workspace switcher, with "skip-tasklist" and "skip-pager", respectively. Both take either "TRUE" or "FALSE" as values.
**DevilsPieActionDecorate** is for setting or hiding window decorations (meaning title bars usually). Set "decorated" to "TRUE" or "FALSE".
**DevilsPieActionLayer** is for setting a window as on top of all other windows, with "above" as "TRUE" or "FALSE" again.
**DevilsPieActionSaveGeometry** is for... um... it prints out lots of stuff if you move or resize that window, I didn't find out what else it does yet. It does not seem to remember the size of applications and then restore them to that size, at least not for the programs I've tried. Has no properties either.
**DevilsPieActionSetGeometry** on the other hand is quite useful, it allows you to set window positions and size. Like for Evince, which always opens too small. Has "xoffset", "yoffset". "width" and "height" properties that take numbers. First two set distance from the left and top border, respectively, to the top left corner of the application window, the other sets the size.
**DevilsPieActionSetWorkspace**, well you know this one from the two examples in Part 1 and Part 2. "pinned" as "TRUE" or "FALSE", "workspace-index" as a number.
**DevilsPieActionResize** is used to resize windows, but unlike the previous not by giving numbers for the size. Properties "maximized", "maximized-horizontally", "maximized-vertically", "minimized", "fullscreen", all take "TRUE" or "FALSE".
**DevilsPieActionDebug** has no properties and enables the debug mode, it will print window_title, application_name and window_role of all the open windows.
**DevilsPieActionSetWintype** does something I don't know ^^;;
**DevilsPieActionOpacity** requires xcompmgr active (read the great howto here: [http://ubuntuforums.org/showthread.php?t=75527)](http://ubuntuforums.org/showthread.php?t=75527)). It allows you to set the translucency of windows (similar to transset, only automatically :)). Property "opacity", takes a value from 0.00 (completely translucent) to 1.00 (completely opaque)

As you see, the possibilities are nearly endless.

The complete Devil's Pie reference is available here (if you have it installed): file:///usr/share/doc/devilspie/devilspie-reference.html


Thanks go to Ross Burton for writing such a cool program (check out his site at [http://www.burtonini.com/)](http://www.burtonini.com/)), the Ubuntu team for creating such a fine distribution and community, and to those who actually read this for enduring my by far too long howto :)

**Appendix: Devil's Pie 0.13+**

Starting with Devil's Pie 0.13, a new method for configuration, called "S-Expressions" is used. Currently this is only relevant for people who are using Dapper, or who have compiled the new version themselves. Many of the old concepts still apply, so I assume you have read my explanation of how to use the old Devil's Pie versions. I didn't really test this part of the guide as much as I should; so if something doesn't work, it's probably my error. Drop me a note and I'll take a look at it.

New Devil's Pie releases read their configuration from "rulename.ds" files, which may be located in ~/.devilspie/ and /etc/devilspie, the last one is for rules that apply to all users. Currently, each .ds file can only contain a single rule, so don't try to put more than one in each file.

Note: Things in *UPPER CASE* are placeholders, you have to replace them with a real value. They're only here to make the structure more obvious. Bolded things are part of the expressions (it's a bit hard to see, i notice now... this includes (, ), + and x, but not the *).

A Rule looks like this:
**(***RULE***)**

Where *RULE* can be one of the following:
- *ACTIONS*
- **if** (*MATCHERS*) (*ACTIONS*)

The first one is for rules that apply to all windows, the second one is for rules that apply only to certain windows. As in the main guide, let's look at matchers first.

*MATCHERS* can be the following:
- **is** (TYPE) VALUE
- **contains** (TYPE) VALUE
- **matches** (TYPE) VALUE

*TYPE* can be one of **application_name**, **window_name** and **window_role**, they're the same as in previous versions, with the exception that window_title is now called window_name. 
*VALUE* is something double-quoted, this is the value you want the windows to be compared against. 
**is** looks whether the appropriate value for TYPE is the same as your VALUE, **contains** whether it contains your VALUE, and **matches** is used if you want Regular Expressions (which I won't explain this time either ^^;;; , look it up on the internet if you're interested)
So this would be a *MATCHERS* that gets all the windows that have an a in their title: contains (window_name) "a"

Now, this is not terribly interesting yet... just checking for one attribute often isnt enough. What if I want all Firefox windows that have "Ubuntu" in their title? You have to combine matchers. In addition to the above, 

*MATCHERS* can also be: (* means that you can have as many as you want)
- **and (***MATCHERS***)***** 
- **or (***MATCHERS***)*****

And checks whether all of the matchers following it are true, or checks whether at least one of them is true. So this *MATCHERS* would get all Firefox windows with Ubuntu in their title:
and (is (application_name) "Firefox") (contains (window_name) "Ubuntu")

You can combine these elements as you want it. The only limit is your imagination :)

Now for the actions...
*ACTIONS* can be
- *ACTION*
- **begin ***ACTION**

quite simple, really: If you have more than one action, start with a begin. Some actions have arguments, put the action name and arguments in parens (like I did below) unless you only have one action, when you can (and have to) leave them away. Here's a of the different ACTION types:

**debug **
 - Display window information (if you start devilspie from the command line)
**(geometry ***WIDTH***x***HEIGHT***+***XPOSITION***+***YPOSITION***)**
 - Set size and position. So (geometry 100x100+0+0) will make it 100 by 100 pixels large and put it into the top right corner
**fullscreen**
 - Make the window full screen
**maximize**
 - Maximize the window
**maximize_vertically**
 - Maximize the window vertically
**maximize_horizontally**
 - Maximize the window horizontally
**minimize**
 - Minimize the window
**shade**
 - Roll the window up
**unshade**
 - Roll the window down
**pin**
 - Put the window on all workspaces
**unpin**
 - Don't put the window on all workspaces
**(set_workspace** *NUMBER***)**
 - Move the window to that workspace
**skip_pager**
 - Hide window from the Workspace Selector
**skip_tasklist**
 - Hide window from the Window List 
**above**
 - Keep window above all other windows
**below**
 - Keep window below all other windows

**undecorate**
 - Remove border and title bar
**(wintype** *WINDOW_TYPE***)**
 - Set the window type to *WINDOW_TYPE*
 
 That's pretty much it for this short guide. Here are the examples from the main How-To as S-Expressions:
 ```

 (if (and (contains (application_name) "evolution") (contains (window_name) "Mail")) (set_workspace 2)
 
 (if (and (contains (application_name) "gaim") (contains (window_role) "conversation")) (pin) 
```
 
And one last bonus tip: gedit can highlight matching brackets. Activating that feature makes creating and fixing complicated rules quite a bit easier. :)

---

### Post by cayamara on 2005-10-14
Cool, thanks a lot. I have looked for this functionality. Looks very detailed, though I haven't tried it yet. Again, thanks :razz:

---

### Post by PiTT on 2005-10-14
This is by far one of the best HOW-TOs I have seen in these forums! Thanks a lot, Wolki!

Too bad the configuration stuff changed a lot in the new version...

---

### Post by Wolki on 2005-10-15
Glad you like it.

To everyone who's reading the Howto, please send me any improvements, be it errors, didactic stuff, typos, grammar or language mistakes, anything! First because I want to learn more, second so I can post an improved version to the wiki soon.

[QUOTE=PiTT]
Too bad the configuration stuff changed a lot in the new version...[/QUOTE]

Yeah, but it looks like it only got better. I didn't get to take a closer look at the new version (wanted to write this first), but it looks like it shouldn't be that hard to switch this howto over to the new method. Will look into that once it becomes important.

---

### Post by A-star on 2005-10-17
so can anyone tell me what I have to do so that nautilus opens with the maximum windowssize possible?

---

### Post by andrewsawyer on 2005-10-17
Hey,

Thank you for that!

I originally posted a message in the Hoary forums asking how to get Thunderbird to automatically open in the second window - now I know!

Thanks,

Andy

---

### Post by era on 2005-10-17
Just for the record, the Sawfish window manager also has roughly this functionality (it's called "matched windows", plain and simple).

It used to be the default window manager for Gnome at some stage, and I never wanted to switch to anything else after I got used to it. I can understand that Metacity might be less intimidating to newcomers, though (but it's not like you are forced to understand the frills in order to be able to use Sawfish).

---

### Post by Wolki on 2005-10-17
[QUOTE=A-star]so can anyone tell me what I have to do so that nautilus opens with the maximum windowssize possible?[/QUOTE]

OK, here's how to arrive at a solution....

start with a empty .devilspie.xml

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
<!-- put flurbs here -->
</devilspie>
```

So let's start writing a rule:

```
<flurb>
    <matchers>
        <!-- put here how to match nautilus -->
    </matchers>
    <actions>
        <!-- put here what too do with them -->
    </actions>
</flurb>
```

Now, let's try a matcher that gets nautilus:

```
<matcher name="DevilsPieMatcherWindowName">
    <property name="application_name" value="File Manager"/>
</matcher> 
```

(Nautilus' application_name is "File Manager". Had to check with the debug flurb, as described in the howto)

Let's maxmize them with an action:

```
<action name="DevilsPieActionResize">
    <property name="maximized" value="TRUE"/>
</action>

```

And now, assemble the parts:


```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
        <matcher name="DevilsPieMatcherWindowName">
          <property name="application_name" value="File Manager"/>
        </matcher> 
    </matchers>
    <actions>
       <action name="DevilsPieActionResize">
         <property name="maximized" value="TRUE"/>
       </action>
    </actions>
  </flurb>
</devilspie>
```

You can use this as a sample .devilspie.xml that does what you want.

era: Thanks for mentioning it! Yes, many window managers already have such functionality. Metacity by itself doesn't (and that's probably not a bad decision), but it's nice that people who want that functionality can get it.

---

### Post by A-star on 2005-10-17
Thanks for the help,
I'll try this evening, and will let you know the results.

---

### Post by Trullo on 2005-10-18
thanks for your time with this GREAT guide! i appreciate it too much!

---

### Post by Kvark on 2005-10-18
This really cuts down on the time spent arranging windows when in gnome :)

Thanks for the .devilspie.xml file you gave me before in another thread Wolki!

---

### Post by souled on 2005-10-18
Awesome guide, thanks.

Couple questions. When do you use the forward slash, and what's wrong with my flurb: 
```

  <flurb name="Terminal">
    <matchers>
      <matcher name="DevilsPieMatcherWindowName"/>
        <property name="window_title" value="eric@motherland:"/>
	<property name="window_role" value="gnome-terminal-8739-454923534-1129609311"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionHide"/>
	<property name="skip_tasklist" value="TRUE"/>
      </action>
    </actions>
  </flurb>

```

I use Alltray for my terminal, and I don't want it in the window list when I have it opened. When trying to run Devilspie with this, I get this error:

```

** (devilspie:7587): WARNING **: Could not parse configuration: Line 27 character 65: Only <matcher> elements are allowed inside <matchers> not <property>

```

---

### Post by Wolki on 2005-10-18
[QUOTE=souled]
Couple questions. When do you use the forward slash, and what's wrong with my flurb: [/quote]

Forward slash at the end of a tag only if there's no tag that closes it. Usually only for <property ......  /> lines, so remove them from your <matcher .... > and <action .....> lines. I copied the debug flurb without explanation from the sample file, I'll update that section later.

gnome-terminal's window_role seems to be unique to the window, so your matcher won't work probably. It's best to create a profile in gnome-terminal for the tray and disable the dynamic window title for that profile. Then match window_title against the profile title,  and window_role against "gnome-terminal".

---

### Post by souled on 2005-10-18
Ok. I've got the syntax stuff straightened out, but I have another problem. I can get the terminal to bypass the window list, but when I send it to the taskbar using AllTray, and then make it visible again, the window appears again in the window list. Why does this happen?

---

### Post by Wolki on 2005-10-19
Note: I added the part on closing tags and switched to a slightly easier way of using the debug flurb; so check these new parts if you've already read the  howto.

[QUOTE=souled]Ok. I've got the syntax stuff straightened out, but I have another problem. I can get the terminal to bypass the window list, but when I send it to the taskbar using AllTray, and then make it visible again, the window appears again in the window list. Why does this happen?[/QUOTE]

Hm, i tried it myself and wasn't able to get alltray to put things into the tray on Breezy. :-/ So i can't really check what the problem could be,

Did you use the matcher I described in my previous post? If you want all your terminals to not appear in the window list, you can skip creating a profile and matching against window_title.

---

### Post by souled on 2005-10-19
Yeah, I disabled the dynamic title, and just made the window "Terminal." However, when you dock it with AllTray, the name in the window list becomes Terminal (AllTray).  I set the window-title value to Terminal (AllTray), and it does bypass the window list when I run Devil's Pie. I just have the problem of it coming back into the window list when I open it after docking it in the taskbar.

---

### Post by ubuntu_demon on 2005-10-20
What a tasty pie this is :).
I'm gonna look into this the next time I'm bored. Seems handy. Thnx for the HOWTO

---

### Post by bam on 2005-10-20
ok, its working but moves the application from where I tell it to go to the active workspace, any ideas?

---

### Post by Wolki on 2005-10-21
[QUOTE=bam]ok, its working but moves the application from where I tell it to go to the active workspace, any ideas?[/QUOTE]

Can you post the relevant section of your .devilspie.xml?

---

### Post by bam on 2005-10-21
after restarting gnome it seems to work now, maybe the config just needed to be reloaded?

---

### Post by Wolki on 2005-10-21
Yes, after editing the confg file devilspie has to be restarted... I should add that to the Howto. Thanks!

---

### Post by Caboto on 2005-10-21
I've just worked through your How-To (been a little busy last week).
Man... This ist just awesome. I've looked several times for a really detailled description on how to use devilspie. Never found a good one till now.

Definitely one of the best How-To's here. Really nice work! :)

---

### Post by jd_ on 2005-11-01
Thank you ! Great software and great How-to (I'm quite used to XML but it is so nicely written I've read everything though).

---

### Post by Sionide on 2005-11-02
Wonder when/if someone will write a front-end gui for this to make it quicker and easier to do..

---

### Post by jd_ on 2005-11-02
[QUOTE=Sionide]Wonder when/if someone will write a front-end gui for this to make it quicker and easier to do..[/QUOTE]

Well, I *might* do a front-end (at least for me, first step). Let's say I've said nothing at all :KS

---

### Post by manicka on 2005-12-02
I have added this how-to, to the Ubuntu Document Storage Facility

---

### Post by henriquemaia on 2005-12-02
Great howto, thanks.

Just a question. Where can I find documentation for the newer versions of devilspie?

---

### Post by jrib on 2005-12-02
[QUOTE=henriquemaia]Great howto, thanks.

Just a question. Where can I find documentation for the newer versions of devilspie?[/QUOTE]

documentation is incredibly lacking for all versions of devilspie including the latest one, I have found.

You are pretty much stuck with using the README file and reading src/parser.c.  I never used the version this howto refers to which uses xml but I find the new S-expressions syntax to be much more concise and after you do a few you should get the hang of it.  On the devilspie page, you can read some of the comments for the rewrite page.  The author had a little blurb about the AND and OR options which I didn't find elsewhere.

Admittedly I only use devilspie to do two things, but a nice idea would be to start a new thread and post examples (which are also really lacking in the docs) of devilspie s-expressions and a description of what they do.  Let me know if you are interested in doing this.  We can probably learn from each other. :D

---

### Post by henriquemaia on 2005-12-02
[QUOTE=_jason]documentation is incredibly lacking for all versions of devilspie including the latest one, I have found.

You are pretty much stuck with using the README file and reading src/parser.c.  I never used the version this howto refers to which uses xml but I find the new S-expressions syntax to be much more concise and after you do a few you should get the hang of it.  On the devilspie page, you can read some of the comments for the rewrite page.  The author had a little blurb about the AND and OR options which I didn't find elsewhere.

Admittedly I only use devilspie to do two things, but a nice idea would be to start a new thread and post examples (which are also really lacking in the docs) of devilspie s-expressions and a description of what they do.  Let me know if you are interested in doing this.  We can probably learn from each other. :D[/QUOTE]

That would be a very good idea. Unfortunately, I'm the least qualified person to do that, because I'm just starting on devilspie (I knew devilspie, but never had it properly configured).

---

### Post by jrib on 2005-12-02
[QUOTE=henriquemaia]That would be a very good idea. Unfortunately, I'm the least qualified person to do that, because I'm just starting on devilspie (I knew devilspie, but never had it properly configured).[/QUOTE]

Well since at least one other person is interested I will create the thread so that we don't take this current thread offtopic.  As soon as it is approved by a mod it should appear in the customization section with the title: "Devilspie (version 0.13 and greater) s-expressions examples".

---

### Post by Wolki on 2005-12-02
I've been working on another (still secret :)) project and didn't work a lot on thiis howto... I've had to look into the new s-expr things though, and could probably write a quick intro/reference. Now that the new versions are in dapper, i can actually test things :) it'll take a few days though, henrique.

jason, I wouldn't call examples off-topic, so you could've posted them here. A new thread is fine too, please post a link here once it's available. :)

and thanks, manicka!

---

### Post by jrib on 2005-12-02
[QUOTE=Wolki]jason, I wouldn't call examples off-topic, so you could've posted them here. A new thread is fine too, please post a link here once it's available. :)[/QUOTE]

You're right, it's ontopic but it may get a bit confusing if we discuss two different formats in the same thread.  I'll definitely link once it's approved.  Any idea on how long it usually takes for a thread to be approved?

---

### Post by henriquemaia on 2005-12-02
[QUOTE=_jason]You're right, it's ontopic but it may get a bit confusing if we discuss two different formats in the same thread.  I'll definitely link once it's approved.  Any idea on how long it usually takes for a thread to be approved?[/QUOTE]

looking forward to this new thread ;)

I really really want to tame some wild windows on my desktop :D

---

### Post by sup on 2005-12-03
thanks for the great howto. I have one question - is it possible to add commnets to the config file? I tried ```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
#comment
<flurb>
blahblah
</flurb>
</devilspie>

```
but when run in terminal, it gave out this:
** (devilspie:12981): WARNING **: Could not parse configuration: Line 6 character 2: No text is allowed inside element <2>

---

### Post by Wolki on 2005-12-03
[QUOTE=sup]I have one question - is it possible to add commnets to the config file?[/QUOTE]

Yes. Do it like this:
```
<!-- This is a comment -->
```


[edit] I've added an appendix with a beta explanation of devilspie >=0.13.

---

### Post by jrib on 2005-12-04
[QUOTE=Wolki]jason, I wouldn't call examples off-topic, so you could've posted them here. A new thread is fine too, please post a link here once it's available. :)[/QUOTE]

Anyone interested in S-expression examples for the latest versions of devilspie can post their own examples and read other users' at [http://ubuntuforums.org/showthread.php?t=98071](http://ubuntuforums.org/showthread.php?t=98071).

---

### Post by Kasanax on 2005-12-31
Excellent walkthrough - after a few failed attempts at using DevilsPie, I finally got it up and running!

I am having a problem though... I'm trying to get gnome-terminal to open full screen. This is the text of my .devilspie.xml file:

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="gnome-terminal"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionResize">
        <property name="fullscreen" value="True"/>
      </action>
    </actions>
  </flurb>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="gaim"/>
        <property name="window_role" value="conversation"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
    </actions>
  </flurb>
</devilspie>

```

The other flurb, the one for Gaim, works fine. Am I doing something wrong with the application name?

Any help would be greatly appreciated! :smile:

---

### Post by Wolki on 2005-12-31
[QUOTE=Kasanax]The other flurb, the one for Gaim, works fine. Am I doing something wrong with the application name?[/QUOTE]

Gnome-terminal doesn't have "gnome-terminal" as application name; it depends on the program you're running, or the directory you're in. You need to match against window_role, which should contain "gnome-terminal" and a large number of apparently random numbers. So, just changing "application_name" to "window_role" in the flurb should make it work, I guess.

---

### Post by souled on 2006-01-01
You can also try wildcards. When dynamically set titles are enabled for the terminal, the directory is displayed in the terminal title. It starts with your username and @ (i.e. my terminal starts with eric@). You could put your username with the @ and then * I think it is for wildcards (not exactly sure... the s-expressions use .+ for wildcards I think...) Another way is to disable dynamically set titles, and you can set the title to whatever you want. Then you can use the application_name function and set the value to whatever you named the terminal. I'm pretty sure these methods work... Haven't messed around with devil's pie and the terminal in awhile because I have my config file exactly how I want it :). Just mess around with it, and you'll get it eventually; trial and error.

---

### Post by Kasanax on 2006-01-05
Alrighty, I've tried playing around with my .devilspie.xml file a lot, and I still can't get this figured out...

I'm still trying to get gnome-terminal to run in full screen all the time. I took Wolki's advice, and tried putting in "window_role" as the propery name, then I tried both "gnome-terminal" and "gnome-terminal*" as the values for the property in the <matchers> part of the flub... neither one seemed to work.

Then, I tried matching the flub to the window title. So, I tried this:

```
<flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="window_title" value="mike@ubuntu: ~"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionResize">
        <property name="fullscreen" value="True"/>
      </action>
    </actions>
  </flurb>
```

Since, "mike@ubuntu: ~" is the full title of the window. I also tried "mike@*", "mike@", and "mike@ubuntu*"

I'm sure there's something really simple I'm messing up here... any ideas?

---

### Post by sup on 2006-01-06
Hello, for some time I have been noticing a freeze down (Ubuntu just stopped coming up, the programs that are listed in system>preferences>sessions>startup programs would not start) during startup just after that update manager (priority 50 I believe) seemed to have been lounched. Lounching of any application (for example gnome-terminal that I can start with ALT+F3) would solve this and the system would start up after that without any further problem.
 Recently I realized that devilspie has a priority 51 so I deleted its entry from startup programs and suddenly I enountered nomore freezedowns. Has anyone come across something similar? I saw people reporting starting devilspie upon startup without any problems here in the forum.
I am using version 0.16, Ubuntu breezy.

---

### Post by Wolki on 2006-01-06
[QUOTE=Kasanax]
I'm sure there's something really simple I'm messing up here... any ideas?[/QUOTE]

OK, i tried it out. It works here with "window_role" matching "gnome-terminal", but you need to capitalize the "True". I recommend this against matching the title, as this may chang depending on the program you're running/ the directory you're in. You could also set a custom title in gnome-terminal and match against that, but that only seems useful if you want different types of terminals behave differently.

[QUOTE="sup"]
Recently I realized that devilspie has a priority 51 so I deleted its entry from startup programs and suddenly I enountered nomore freezedowns. Has anyone come across something similar? I saw people reporting starting devilspie upon startup without any problems here in the forum.
I am using version 0.16, Ubuntu breezy.[/QUOTE]

I had a big slowdown when devilspie had a very low startup number, but with 50+ it works without problems here. Didn't try 0.16 on breezy yet, though. Can you try setting the number a little higher?

Oh, does devilspie startup correctly (and fast) if you run it from the command line directly? If not it might be a problem with your rules.

---

### Post by sup on 2006-01-06
Well, I set it to 65 so that it starts as the last appllication anw it does not freezes anymore, but tha bad side of it is that the devilspie rules are applied after all the applications were started up... but I think I can live with that.

(I think the problem could be in the fact that devilspie runs in terminal, not as a daemon)

---

### Post by Kasanax on 2006-01-06
Success!! Thanks Wolki - I knew it was something simple like that...

Thanks for all the help! :D

---

### Post by sabrewolf2006 on 2006-07-26
This is a fantastic HOWTO. Windows now appear where I want them to :D

I just have one problem. I'm trying to pin a terminal that I've created to the first two desktops only. How would one go about doing this?
This is what I have so far:
(if
    (is (window_name) "Desktop Terminal")
    (begin
        (wintype "desktop")
        (set_workspace 1)
	(pin)
	(set_workspace 2)
	(pin)
	(set_workspace 3)
	(unpin)
    )
) 
This appears to pin the terminal to desktop three only.
(Desktop Resized for easy viewing)

---

### Post by Wolki on 2006-07-26
> **sabrewolf2006 said:**
> This is a fantastic HOWTO. Windows now appear where I want them to :D

Thanks. I really should fully update this guide for dapper, but I don't think i'll find the time right now :-/.


> I just have one problem. I'm trying to pin a terminal that I've created to the first two desktops only. How would one go about doing this?

pin puts on all workspaces, so you can't have it only on some all workspaces :) I guess that last unpin is what devilspie actually takes, so it's put only on the last workpace you selected.

I doubt what you plan to do is possible with devilspie. It should probably not be impossible to write something that does that by hand using wnck (check when the user moves to a workspace whether that workspace is one where the window is supposed to be put, and if it is move it there), but even in python wnck can be a bit problematic. Can'T really help you much with this right now, but maybe someone else will? :)

---

### Post by sabrewolf2006 on 2006-07-28
Its not that much of a problem really, its just that on desktop three I have either rhythmbox or quodlibet running in fullscreen (not party mode in rhythmbox, it follows the focus round) so I figured it'd be a waste of cycles in having a terminal behind.

---

### Post by jeff_ on 2006-08-05
I'm using devilspie version .16-1 and having trouble getting it to recognize the window_name of openoffice documents. It will recognize the "OpenOffice" part of the document, but if I open a document called DocumentName so the window name appears as "DocumentName - OpenOffice.org Writer" and have a matcher for contains "DocumentName" it wont work. If I change the matcher to contains "OpenOffice" then it does work. The following is basicly what I have:

```
 (if (and (contains (application_name) "OpenOffice") (contains (window_name) "DocumentName")) (set_workspace 4))
```

Thanks --Jeff

EDIT: I'm now fairly certain the problem is that when openoffice first launches a document, say MyDocument, the window title is initially just OpenOffice.org and then it changes to the full "MyDocument - OpenOffice.org Writer". I'm guessing since devilspie starts before this happens it only looks at the initial window title and not the title after it changes. If this is so, can anyone thing of a possible workaround for this? Thanks again --Jeff

---

### Post by Wolki on 2006-08-10
> **jeff_ said:**
> 
EDIT: I'm now fairly certain the problem is that when openoffice first launches a document, say MyDocument, the window title is initially just OpenOffice.org and then it changes to the full "MyDocument - OpenOffice.org Writer". I'm guessing since devilspie starts before this happens it only looks at the initial window title and not the title after it changes. If this is so, can anyone thing of a possible workaround for this? Thanks again --Jeff

Yes, it sounds like that is the problem. Unfortunately I can't think of a workaround for this, except restarting devilspie. Long-term, OOo could be fixed to set the correct window title immediately if possible, or devilspie could be enhanced to support matching on window changes. (I'm not a good enough coder to do any of them -_-)

---

### Post by jeff_ on 2006-08-10
> **Wolki said:**
> Yes, it sounds like that is the problem. Unfortunately I can't think of a workaround for this, except restarting devilspie. Long-term, OOo could be fixed to set the correct window title immediately if possible, or devilspie could be enhanced to support matching on window changes. (I'm not a good enough coder to do any of them -_-)

When I installed the devilspie package did it install the source code as well? If so where and if not what's the best way to take a look at it? I'm new to the whole linux open source thing, but I do have plenty of experience coding. Thanks -- Jeff

---

### Post by jrib on 2006-08-11
> **jeff_ said:**
> When I installed the devilspie package did it install the source code as well? If so where and if not what's the best way to take a look at it? I'm new to the whole linux open source thing, but I do have plenty of experience coding. Thanks -- Jeff

You can download the source for most packages by doing 'sudo apt-get source package_name'.  It will get put in your current working directory.  The actual source code will probably be in devilspie-version/src

---

### Post by jeff_ on 2006-08-11
> **Wolki said:**
> Yes, it sounds like that is the problem. Unfortunately I can't think of a workaround for this, except restarting devilspie. Long-term, OOo could be fixed to set the correct window title immediately if possible, or devilspie could be enhanced to support matching on window changes. (I'm not a good enough coder to do any of them -_-)

Ok, I got the devilspie source and updated it to support matching on window title changes. It now works with OO as well as any other window change. I emailed the maker of the program about this change and if you're interested I can tell you how to change the source to add this functionality. --Jeff

---

### Post by PingunZ on 2006-08-17
Looks nice is this possible :

When I startup I want a fullscreen ( F11  without menubar and gnome-panel ) gnome-terminal on desktop 1.
I want it to use the gnome-terminal-profile name ' StartUp '

When I manually start up a gnome-terminal I want it to behave normal ( not fullscreen, with menubar, using the profile 'PingunZ' and with a gnome-panel)

Would someone be so kind to create a script for me ?
or tell me if its possible/some tips/ ..

---

### Post by PingunZ on 2006-08-18
hmm apparently not.

---

### Post by Wolki on 2006-08-18
> **PingunZ said:**
> hmm apparently not.

I'm sorry, I was quite busy the last few days.

Basically, I see no problem with doing that. Launch gnome-terminal with the correct profile on startup, and sset that profile to include the profile name in the window title, and to drop the menu bar.

It should work similar to this:
```

 (if (and (contains (window_role) "gnome-terminal") (contains (window_name) "StartUp")) (begin (set_workspace 1) (fullscreen)))

```

Then select PinguinZ as the default profile and it should work like you described it. I didn't test it though, so there might be an error somewhere.

---

### Post by cactaur on 2006-08-19
When I try to run devilspie, I get a message that says,"No s-expressions loaded, quiting". I think that's because I have my .xml document in my home directory? If that's the problem, can you tell me where to put it, if not, then what I did wrong? I tried replacing what I did with your example, it still didn't work.

---

### Post by kpkeerthi on 2006-08-19
devilspie tries to locate .ds files in ~/.devilspie directory. You need to create your scripts and then save as script1.ps, script2.ps, etc and put these files in the .devilspie directory in your $HOME folder and devilspie will auto-load these files on startup.

---

### Post by Wolki on 2006-08-19
> **cactaur said:**
> When I try to run devilspie, I get a message that says,"No s-expressions loaded, quiting". I think that's because I have my .xml document in my home directory? If that's the problem, can you tell me where to put it, if not, then what I did wrong?

The instructions were for the version in Breezy, and the configuration has changed from xml to s-expressions. There's  an appendix at the end of the thread about how to create them, and I've had plans to rewrite the guide but didn't get to it yet.

Try putting the default s-expressions into the directory as .ds files like kpkeerthi said, if it still doesn't work ask again and I'll take another look.

---

### Post by cactaur on 2006-08-19
Oh thanks, works beautifully now.

---

### Post by bleers on 2006-12-02
devilspie really is great and works fine with Firefox etc.

problem with Radrails:
But I can't get a program called Radrails (IDE for Rails) to go to a specific workspace.
Do you've any suggestions?

my **radrails.ds **file in $HOME/.devilspie:

(if (is (application_name) "radrails") (set_workspace 2))

---

### Post by jrib on 2006-12-02
> **bleers said:**
> devilspie really is great and works fine with Firefox etc.

problem with Radrails:
But I can't get a program called Radrails (IDE for Rails) to go to a specific workspace.
Do you've any suggestions?

my **radrails.ds **file in $HOME/.devilspie:

(if (is (application_name) "radrails") (set_workspace 2))


That seems like it should work.  Are you sure the application name is really "radrails"?
```

killall devilspie
devilspie -d

```

devilspie should now print debug information to your terminal.  Start radrails and see if that is the correct application_name.  I think it is case-sensitive too.

---

### Post by bleers on 2006-12-04
> **_jason said:**
> That seems like it should work.  Are you sure the application name is really "radrails"?
```

killall devilspie
devilspie -d

```

devilspie should now print debug information to your terminal.  Start radrails and see if that is the correct application_name.  I think it is case-sensitive too.

solved it. you're right _jason!
with the debug (-d) option I was able to see the "real devilspie" application name.. it is: RadRails.
So edited my radrails.ds file with this app.name. great :D

---

### Post by Mozork on 2006-12-18
I've started using ubuntu some time ago, so I'm far, far away from being an expert, so it might not be surprising that I seem to fail configuring devilspie for my needs.

Actually I fail on a very basic level, and I have no idea why so...

1. of all: Yes devilspie is working (I tried the gmail example out of the first post in this thread)

So here's my problem:
I want firefox to open only in workspace 3. what I've tried is:

```
(if
 (matches (window_name) "^*Firefox*$")
 (set_workspace 3)
)
```

I've also tried

```
(if
 (is (application_name) "Firefox")
 (set_workspace 3)
)
```

And I inserted for "Firefox" various other possibilities, such as "firefox-bin", "Firefox-bin", "firefox", "Gecko" - none of them worked...

What am I doing wrong?

- Excuse my lack of correct english, there. (it's not my native language...)

---

### Post by bleers on 2006-12-19
Hi Mozork,

As _Jason suggested me (to see the real application_name) in a previous post.
>> I quote _Jason's:
$ killall devilspie
$ devilspie -d

devilspie should now print debug information to your terminal. Start radrails and **see if that is the correct application_name**. I think it is case-sensitive too.

try, to see more options
$ devilspie --help

hope this helps..

> **Mozork said:**
> I've started using ubuntu some time ago, so I'm far, far away from being an expert, so it might not be surprising that I seem to fail configuring devilspie for my needs.

Actually I fail on a very basic level, and I have no idea why so...

1. of all: Yes devilspie is working (I tried the gmail example out of the first post in this thread)

So here's my problem:
I want firefox to open only in workspace 3. what I've tried is:

```
(if
 (matches (window_name) "^*Firefox*$")
 (set_workspace 3)
)
```

I've also tried

```
(if
 (is (application_name) "Firefox")
 (set_workspace 3)
)
```

And I inserted for "Firefox" various other possibilities, such as "firefox-bin", "Firefox-bin", "firefox", "Gecko" - none of them worked...

What am I doing wrong?

- Excuse my lack of correct english, there. (it's not my native language...)

---

### Post by Mozork on 2006-12-19
Well 

I did as you proposed and at first it seemed to work, as there was an error and after fixing it there were no more debuging errors:

```
mozork@mozbook:~$ killall devilspie
mozork@mozbook:~$ devilspie -d
Devil's Pie 0.17.1 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/mozork/.devilspie
Loading /home/mozork/.devilspie/terminal.ds
Loading /home/mozork/.devilspie/gaim.ds
Loading /home/mozork/.devilspie/thunderbird.ds
Loading /home/mozork/.devilspie/firefox.ds

```But sadly it did not work...

```
(if
 (is (application_name) "firefox-bin")
 (set_workspace 3)
)

```Could it be because I've named my workspaces other than workspace n. Or could there be any other reason why it is not working?

---

### Post by jrib on 2006-12-19
> **Mozork said:**
> Well 

I did as you proposed and at first it seemed to work, as there was an error and after fixin git ther were no mor debuging errors:

```
mozork@mozbook:~$ killall devilspie
mozork@mozbook:~$ devilspie -d
Devil's Pie 0.17.1 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/mozork/.devilspie
Loading /home/mozork/.devilspie/terminal.ds
Loading /home/mozork/.devilspie/gaim.ds
Loading /home/mozork/.devilspie/thunderbird.ds
Loading /home/mozork/.devilspie/firefox.ds

```

But sadly it did not work...

```
(if
 (is (application_name) "firefox-bin")
 (set_workspace 3)
)

```

Could it be because I've named my workspaces other than workspace n. Or could there be any other reason why it is not working?

I tried what you posted earlier (should work):
```

(if
 (is (application_name) "Firefox")
 (set_workspace 3)
)

```

and it works fine here.

Did you restart devilspie after creating the .ds file in your ~/.devilspie?

---

### Post by Mozork on 2006-12-19
Hah :D It worked.

Strange... I tried this before and I also restarted devilspie... Well it works now, so I'll just be content with that. ;)

---

### Post by gometro33 on 2006-12-23
If someone needs more help, I found another tutorial that had a lot of examples and explanations.  Very helpful.
[URL="http://wiki.foosel.net/linux/devilspie"]
http://wiki.foosel.net/linux/devilspie[/URL]

---

### Post by krhek on 2006-12-27
I have problems with the "set_workspace" function, which is the main reason why I got interested in this app in the first place, and I really want to get it running. When I execute Devil's Pie in the debug mode I get:

** (devilspie:8060): WARNING **: Workspace number 2 does not exist

(devilspie:8060): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed 

Am I doing something wrong?  Can it be because I have XGL+Compiz installed?
Sorry for bumping the thread and thanks for any replays :)

---

### Post by heng on 2007-01-15
It seems to me that firefox should be called "Firefox" for matching to application_name.

This is contrary to all the various articles I have seen on Devils Pie.

---

### Post by jrib on 2007-01-15
> **krhek said:**
> I have problems with the "set_workspace" function, which is the main reason why I got interested in this app in the first place, and I really want to get it running. When I execute Devil's Pie in the debug mode I get:

** (devilspie:8060): WARNING **: Workspace number 2 does not exist

(devilspie:8060): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed 

Am I doing something wrong?  Can it be because I have XGL+Compiz installed?


Yes, it is probably because you are using Compiz

---

### Post by mojoman on 2007-01-26
Hi,

I just installed devilspie (from the repos and I'm using dapper) and I'm already stuck :oops: 

From the howto I gather that I need to create one or more files with rules that devilspie read (i.e. .ds files). This output
```
$ devilspie
No s-expressions loaded, quiting
```
I take it shows that I have no .ds files. However, I have no .devilspie in my home directory nor do I have a /etc/devilspie directory. Still, it is installed, as the response from 'devilspie' show and I get:
```
$ whereis devilspie
devilspie: /usr/bin/devilspie /usr/bin/X11/devilspie /usr/share/man/man1/devilspie.1.gz
```

So, what I'm I missing here? I basically just need devilspie to do one thing for me (at least for now) and that is to make sure that all windows are opened in the right screen on my TwinView setup. But where is the damn program?! :confused: 

Any and all help very much appreciated.
/Mojoman

---

### Post by jrib on 2007-01-26
> **mojoman said:**
> Hi,

...I have no .devilspie in my home directory nor do I have a /etc/devilspie directory...
/Mojoman

Just create it: ```
mkdir ~/.devilspie
``` :)

---

### Post by mojoman on 2007-01-26
Hehe,

I just ran
```
$ devilspie -d
Devil's Pie 0.16 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/mojoman/.devilspie
/home/mojoman/.devilspie doesn't exist
No s-expressions loaded, quiting
```

and thought "naw, it can't be that simple.". Well, what do you know... 

Anyway, thanks for the help. You wouldn't know the expression needed to make windows open on the right screen in a twinview setup, would you?

/Mojoman

---

### Post by Mozork on 2007-02-25
Okay, new task for the devilspie-pros out there:
I want THE Gimp to be a bit more automated, therefore I wrote some expressions, of which some work, and some don't ;)

```
(if
  (is (application_name) "The GIMP")
  (begin
    (set_workspace 4)
  )
)
(if
  (and
    (is (application_name) "The GIMP")
    (is (window_name) "The GIMP")
  )
  (begin
    (above)
    (geometry "272x640+5+24")
  )
)
(if 
  (and 
    (is (application_name) "The GIMP")
    (contains (window_name) "Layers, Paths, ")
  )
  (begin
    (above)
    (geometry "273x323+5+693")
  )
)
(if
  (and
    (is (application_name) "The GIMP")
    (is (window_name) "Navigation")
  )
  (begin
    (above)
    (geometry "273x323+5+693")
  )
)
(if
  (and
    (is (application_name) "The GIMP")
    (contains (window_name) "Untitled")
  )
  (geometry "1085x950+287+24")
)
```

and here the corresponding debug output:

```
Window Title: 'Navigation'; Application Name: 'The GIMP'; Class: 'Gimp'; Geometry: 250x300+129+416
Window Title: 'Untitled-1.0 (RGB, 1 layer) 420x300'; Application Name: 'The GIMP'; Class: 'Gimp'; Geometry: 580x406+512+83
Window Title: 'Layers, Paths, Channels, Undo | Brushes, Patterns, Gradients'; Application Name: 'The GIMP'; Class: 'Gimp'; Geometry: 293x943+1321+24
Window Title: 'The GIMP'; Application Name: 'The GIMP'; Class: 'Gimp'; Geometry: 272x640+124+81
```

What works is, that all gimp windows except the main window (window_name the GIMP) are moved to my fourth workspace. The main window gets moved, only, when gimp is open and i execute devilspie, not vice versa. geometry and above doesnt work. It worked though, when I only had
```
(above)
```
instead of 
```
(begin
    (above)
    (geometry "273x323+5+693")
  )
```

---

### Post by jrib on 2007-02-25
> **Mozork said:**
> Okay, new task for the devilspie-pros out there:
I want THE Gimp to be a bit more automated, therefore I wrote some expressions, of which some work, and some don't ;)

...


That is kind of  strange, and I'd like to do this too...

A couple of things I noticed: 

[LIST]
[*]if you change the action to (maximize) instead of (set_workspace), it does perform the action on the tool window.  So devilspie does manage to match the window.
[*]Gimp's preferences seems to include window manager settings, so that may be interfering.  I've tried disabling whatever settings are listed there, but devilspie still is not able to move the tool window to another workspace[/LIST]

---

### Post by Mozork on 2007-02-25
> **_jason said:**
> [LIST]
[*]if you change the action to (maximize) instead of (set_workspace), it does perform the action on the tool window.  So devilspie does manage to match the window.
[*]Gimp's preferences seems to include window manager settings, so that may be interfering. I've tried disabling whatever settings are listed there, but devilspie still is not able to move the tool window to another workspace[/LIST]That would fit to my discovery, that once gimp is open, and you start devilspie, the gimp main window gets moved.
Well, ich tried some other tweaks and found out, that when i just have the expression:
```
(begin
  (if
    (is (application_name) "The GIMP")
    (begin
      (set_workspace 4)
    )
  )
  (if
    (and
      (is (application_name) "The GIMP")
      (is (window_name) "The GIMP")
    )
    (above)
  )
)
```all my Gimp windows are on Top, which means, that the second condition is true for all gimp windows. ;) I've also found out, that my other expressions (except for the first and second one)  from my previous post are not working at all... ^^
So, why can't I select them by window_name, reps. why have they all exactly the same window_name? - window_roles could be something to work with, but unfortunately I have absolutely no idea, how to get these window_roles...

---

### Post by jrib on 2007-02-25
> **Mozork said:**
> ... window_roles could be something to work with, but unfortunately I have absolutely no idea, how to get these window_roles...

```
(jrib@castelo:~)% xprop  | grep -i role                                    (9:15/1399)
WM_WINDOW_ROLE(STRING) = "gimp-toolbox"
```

---

### Post by kobewan on 2007-02-25
Yeah, I couldn't get the GIMP to work properly either, I think it had the same problems that you guys are describing above. Anyways, somebody at the Devil's Pie wiki suggested this:> I&#8217;ve managed to customize GIMP to move to another workspace this way:

(or

(matches (window_role) "^gimp.*$")
(is (window_name) "The GIMP")

)

This matches the splash-screen, the toolbox, the main window and the opened image window. So you could first modify each window individually and then move them all to wherever you want.  I havn't tried it, since I kind of lost interest. You guys might what to try it though.

---

### Post by Mozork on 2007-02-25
Now we're getting somewhere... :D
```
(begin
  (if
    (is (application_name) "The GIMP")
    (begin
      (set_workspace 4)
    )
  )
  (if
    (is (window_role) "gimp-toolbox")
    (begin
      (above)
    )
  )
  (if 
    (is (window_role) "gimp-dock")
    (begin
      (above)
    )
  )
  (if
    (is (window_role) "gimp-image-window")
    (begin
      (geometry "1048x950+321+24")
    )
  )
  (if
    (is (window_role) "gimp-tip-of-the-day")
    (begin
      (above)
    )
  ) 
)
```Works everything. :D
But now, there is still the problem with addressing the different gimp-docks. And the one with the gimp-toolbox, well I'll keep on trying. ;)

€dit:
Ok, I've altered my expressions upon kobewan's post. It looks somewhat nicer, but It hasn't really changed the main points:
```
(begin
  (if
    (or
      (matches (window_role) "^gimp.*$")
      (is (window_name) "The GIMP")
    )
    (begin
      (above)
    )
  )
  (if
    (is (window_role) "gimp-toolbox")
    (begin
      (geometry "311x664+0+0")
    )
  )
  (if
    (matches (window_name) "^*Navigation*$")
    (begin
      (geometry "306x323+5+693")
    )
  )
  (if
    (matches (window_name) "^*Layers, Paths*$")
    (begin
      (geometry "296x950+1379+24")
    )
  )
  (if
    (is (window_role) "gimp-image-window")
    (begin
      (geometry "1053x950+316+24")
      (below)
    )
  )
  (if
    (or
      (matches (window_role) "^gimp.*$")
      (is (window_name) "The GIMP")
    )
    (begin
      (set_workspace 4)
    )
  )
)
```

What works is:
[LIST]
[*]All gimp windows are set to be on top.
[*]The gimp-toolbar is resized upon my demanding. ;)
[*]The gimp-image-window is resized.
[*]All gimp windows except for the gimp-toolbar are moved to workspace 4.[/LIST]What doesn't work is:
[LIST]
[*]The gimp-toolbar remains in the workspace the gimp was opened.
[*]The gimp-image-window is not set to be not on top anymore. (Dont know why...)
[*]The both expressions with the window_names intended to address different gimp-docks don't work.[/LIST]

---

### Post by dante.regis on 2007-04-27
I don't know if anyone of you experienced this (I haven't read the whole post) but I was having a problem with undecorate: I was trying to get a transparent terminal on my desktop, and wanted it on the right side of the screen, for most automatic icons created by ubuntu lay on the left side. I placed my rules and stuff but, no matter how I changed geometry, or the profile, I always got it on the left side of the screen.

Now, I found out what happens: the UNDECORATE action should be placed BEFORE the GEOMETRY action. This is because undecorate will place the window at top-left, and THEN you will move it with geometry. Hope this help somebody!

Best,
Dante

---

### Post by mzwarg on 2007-07-27
I posted instructions on how to use dbdesigner 4 (under wine) and devilspie together.

[Look my comments]("http://bioinformaticsonline.co.uk/2007/04/13/help_running_dbdesigner4_from_wine_on_ubuntu#comment-1652")

---

### Post by twist2b on 2008-04-13
For anyone that has an idea of what I should do:
I boot with:
VBoxManage startvm xp
so Then When it loads, it loads in the first window, Is this how I can load VirtualBox in the second window?:


Code:

```
?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="VBox Manager startvm xp"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="workspace_index" value="2"/>
      </action>
    </actions>
  </flurb>
</devilspie>
```

That should just change were It opens the application right? its a specific boot. But i dont know if I put it under application_name
So when I login, I have under sessions startup:
devilspie
VBox Manager startvm xp
So when it starts up it should just boot it in the second workspace.



ALSO:
were do I save the .devilspie.xml flie? and is it ".devilspie.xml" or "devilspie.xml"

---

