---
title: "sudo gedit problem"
date: 2022-06-13
forum: New to Ubuntu
---

### Post by Complete on 2022-06-13
I just set up a Ubuntu VM1 and I explanded the desktop to cover two monitors. This might be the problem I am having with the editor. When I type 'sudo gedit" I get this error and no editor comes up.

[IMG]https://preview.redd.it/txnbtfr6uc591.png?width=718&format=png&auto=webp&ac0da9d6[/IMG]

After I gave my password, it has this strage error "Authorization requried, but no authorization protocol specified"

I do not now what this means and in a previous virtual machine with Ubuntu, this never happened before.

---

### Post by TheFu on 2022-06-13
Best not to use sudo with any GUI program. There are unwanted side-effects possible. This has been the situation on Ubuntu since the start.

Use sudoedit to edit system files.  You can setup sudoedit to use whatever editor you prefer.

---

### Post by Complete on 2022-06-13
> **TheFu said:**
> Best not to use sudo with any GUI program. There are unwanted side-effects possible. This has been the situation on Ubuntu since the start.

Use sudoedit to edit system files.  You can setup sudoedit to use whatever editor you prefer.

OK, but the deal is that I need to edit the /etc/environment file and, from my experience, if you do not launch gedit with some sort of administrative privledges, you are not able to save this file since it is protectec.  If I am not going to use sudo, then what is an alternate work-arund.

---

### Post by oldfred on 2022-06-13
There used to be gksudo.
Then they recommended sudo -H
man sudo
> [FONT=monospace][COLOR=#000000]**-H**[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]**--set-home**[/COLOR][COLOR=#000000] [/COLOR]
                 Request that the security policy set the HOME environment variable to the home di&#8208; 
                 rectory specified by the target user's password database entry.  Depending on the 
                 policy, this may be the default behavior.


[/FONT]

But TheFu's suggestion using a terminal editor is best.
Default is often nano (which TheFu hates & immediately changes default) and that works ok as at bottom it has keys to use to save updated file or just exit.

sudoedit /etc/filename

---

### Post by ajgreeny on 2022-06-13
If you really want to use gedit as your application for editing text files as root it is very easy to change the from the default, nano to gedit simply be adding the line ```
export EDITOR="gedit"
``` to your hidden **.bashrc** file.

Now after logging out and back in, command ***sudoedit filename*** will open that file in gedit rather than nano but now with root permissions so you can save it as if it was a normal user owned file.

You still need to take great care and make sure that you backup the original file first just in case you make a mistake, something I have done before now.

---

### Post by deadflowr on 2022-06-13
Fur the record,
Newer Ubuntu releases have removed the patch that caused the env_keep issues that happen.
See bug report on that: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1556302]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1556302")
Applies to all after 19.10.
Ubuntu 18.04 still has the patch.


But +1 (+?) to using a terminal based editor with sudo.

Optionally you can always install the nautilus-admin package which will set a context option in the nautilus file manager to edit files as admin/root.
Of course this only works for desktops running the nautilus file manager, which Ubuntu's default desktop does.

---

### Post by coffeecat on 2022-06-13
> **deadflowr said:**
> 
Newer Ubuntu releases have removed the patch that caused the env_keep issues that happen.

I found this comprehensive description on AskUbuntu: [https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10](https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10)

Worth bookmarking.

---

### Post by Impavidus on 2022-06-14
The best way is with sudoedit. That way, the text editor doesn't run as root; only some file copy operations do so.

Suppose your text editor is somehow compromised. Maybe it has some scriptable features and somebody has managed to insert a malicious script into your system. Then the text editor running as root can do anything in your system. Or, sudo can be configured to allow specific commands by specific users. If that includes running a text editor for a specific file, the user can still do anything, as some text editors allow you to escape to a shell.

You can configure sudoedit to use gedit. There's a catch though: gedit is one of those text editors that use a single process with multiple windows. If you open gedit when it's already running, the new instance will detect this, tell the original instance to open a new window with the file you want to edit and then the new instance will terminate. sudoedit detects this termination and assumes you're done editing the file, sees you haven't changed anything, deletes the temporary file and terminates. The text editor can then save the modified file, but sudoedit, having already terminated, won't do anything with it. Terminal based editors like nano and vim don't have this disadvantage.

---

### Post by TheFu on 2022-06-14
I really dislike when GUI programmers decide to protect Unix users from themselves.  If I want to run 50 instances of Firefox or gedit, and my system can do that, then it should be allowed.  If the system cannot do it, I'd expect some programs to crash, but I don't expect the programs to refuse to run.  That just means the GUI programmers were lazy and decided not to properly address concurrent access problems, often for the settings in a specific program.

This is one reason why using GUI programs with sudo is not a good idea.  But if you must, use sudoedit.  Actually, using sudoedit for editing any system files provides a number of protections, some spelled out above.  I don't always use sudoedit - old habits - but I'm a vim user.  I wasn't always, but over time, I found myself using vim-mode more and more in other editors to get work done more efficiently, until a brick finally knocked some sense into my brain and I started using vim all the time.  Another reason is that I've never logged into any router that had a GUI editor, but they all have vim.

---

### Post by vanadium on 2022-06-14
A trick to have gedit not connect to a running proces is the `-s` option. A script like

```

#!/bin/sh
env SUDO_EDITOR="/usr/bin/gedit -s" sudoedit "$@" 2>/dev/null

```

would then avoid the issue when an instance is running already (and keep the terminal clean).

Those who prefer aliases over a script can wrap this up as

```

alias sedit='2>/dev/null env SUDO_EDITOR="/usr/bin/gedit -s" sudoedit'

```

---

