---
title: "[SOLVED] [Solved] ls mixing sort order for dot files and case"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by markstinson on 2008-06-03
[FONT="Courier"]
I like POSIX systems to display an 'ls' the old "normal way" - weighted: dot dirs/files before UpperCase. After the UC files, the LowerCase.

Looking at the manpage or help for 'ls' is useless to resolve the "combining" issue. To make matters worse, terms like "ls sort dot files" etc will get you nowhere on Google.

The fix is make sure your LANG or LC_COLLATE environmental variable(s) are set to "C". You can set this in a number of places: System wide, the user's rc scripts or aliased for specific commands.

**_System Wide:_**

If you set to your LANG or LC_COLLATE system wide, you'll have to set it TWO places. It will also require a reboot for it take effect. There's a reported Launchpad bug about this issue that also impact PAM

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/77983](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/77983)
$LANG is defined in 2 places: /etc/environment and /etc/default/locale

You'll want to comment out LANG="en_US.UTF-8" or whatever and add LANG="C". Alternatively, you could try just adding LC_COLLATE="C"

# LANG="en_US.UTF-8"
LANG="C"

# or just add

LC_COLLATE="C"

Changing the system wide LANG could have unintended consequences though.

**_Per user:_**

This will override the system setting and is preferred.

A user can edit their ~/.bashrc script to add either line:
export LANG="C"
# or
export LC_COLLATE="C"

This modification only affect that specific, existing user. If you want all new, future users to have this in their ~/.bashrc by default, then as root, you should add the updated environmental variables to the system wide /etc/skel/.bashrc file. The /etc/skel files are copied to every new user account.

**_Per alias:_**

Maybe you want to leave everything alone and wish to have your aliases deal with it specifically. Again, you can add these directly to your ~/.bashrc. Or even smarter, uncomment the .bash_aliases section in your ~/.bashrc file, create a ~/.bash_aliases file and add any of your personal aliases there. 

To set it just for ls, use either of the following:

[LIST]
[*] alias ls='LC_COLLATE=C ls' # for non-color
[*] alias ls='LC_COLLATE=C ls -F --color=auto' # for color
[/LIST]

**_Additional information:_**

If you need additional information the other locale environmental variables, please consult: 

[LIST]
[*] man setlocale # this is in Section 3 
[*] [http://www.google.com/search?q=man+setlocale](http://www.google.com/search?q=man+setlocale) # if you don't have locale headers installed
[*] [http://www.linux.com/feature/53781](http://www.linux.com/feature/53781)
[*] [http://www.google.com/search?q=linux+locale+setting](http://www.google.com/search?q=linux+locale+setting)
[/LIST]

May this bring the desired order and alignment to your $HOME 

Later, markstinson
[/FONT]

---

### Post by ZabiGG on 2008-06-04
Thanks very much for the info :)

To officially mark your post solved, please click on the Thread Tools link just above your post, then select Mark thread solved.

Cheers,

Z.

---

