---
title: "Newbie problem - Navigation in terminal"
date: 2015-08-09
forum: New to Ubuntu
---

### Post by VonAntero on 2015-08-09
I've had a small server for quite some time now. I use it mainly for stuff like Teamspeak and other little programs that are really easy to install.
Recently I tried to get a photo gallery called Piwigo to run on my server and after a while I got it running.
While trying to add photos it gives and error message and according to their site I need to delete certain directory.

Here is my newbie problem. I can't see any directories.
Using putty, command ls only lists [COLOR=#0000ff]piwigo-screen[/COLOR] and nothing else.
pwd shows that I'm in root directory. Can't cd anything.

I just cannot find the info on how to get out of this. I know it's something really simple, but I've been googling and reading for two hours now. I've tried to detach the screen, exit the screen... nothing works. I just can't see any directories or files.

Facepalm away, but someone please tell me what to do before I jump off the roof :P

---

### Post by NathanRodriguez on 2015-08-09
From your description looks like you are using a user account with restricted permissions, have you tried other ?

---

### Post by steeldriver on 2015-08-09
Hello and welcome to the forums

> **VonAntero said:**
> 
pwd shows that I'm in root directory.

Do you mean the system root directory 

```

/

```

or "the root" directory
```

/root

```

(home directory of user 'root'). What user are connecting as using PuTTY? what "certain directory" are you trying to delete?

It might also be helpful to share the exact error message(s) that you are getting - and a link to the page on the piwigo site whose instructions you're following.

---

### Post by VonAntero on 2015-08-09
Thanks for the quick reply guys.

> **NathanRodriguez said:**
> From your description looks like you are using a user account with restricted permissions, have you tried other ?
It's a dedicated server and atm it doesn't have any other users. It's a fresh install and the server provider (OVH) emails the root password that I then use to login via putty. So, if I'm not missing something, there should not be any restrictions.

> **steeldriver said:**
> Do you mean the system root directory
That would be /root

The error code is
```
**Fatal error:** Uncaught exception 'SmartyCompilerException' with message 'Syntax Error in template "./admin/themes/default/template/photos_add_direct.tpl" on line 245 "&lt;select data-selectize=&quot;categories&quot; data-value=&quot;{$selected_category|@json_encode|escape:html}&quot;" unknown modifier "json_encode"' in /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php:665 Stack trace: #0 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_compile_private_modifier.php(132): Smarty_Internal_TemplateCompilerBase->trigger_template_error('unknown modifie...', 245) #1 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php(473): Smarty_Internal_Compile_Private_Modifier->compile(Array, Object(Smarty_Internal_SmartyTemplateCompiler), Array, NULL, NULL) #2 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php(257): Smarty_Internal_TemplateCompilerBase->callTagCompiler('private_modifie...', Arra in **/var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php** on line **665**
```

These are the threads:
[http://piwigo.org/forum/viewtopic.php?id=24853](http://piwigo.org/forum/viewtopic.php?id=24853) (team member redirects the op to the next thread)
[http://piwigo.org/forum/viewtopic.php?id=24852](http://piwigo.org/forum/viewtopic.php?id=24852) (team member suggests to delete the _data/template_c directory)

---

### Post by VonAntero on 2015-08-13
Still having this issue. 
The problem is that I don't understand how to move in the folder structure or something like that.
I need to delete a directory, but I just can't figure out how to "find" it.
I'm stuck in /root and ls only lists one thing; [COLOR=#0000ff]piwigo-screen[/COLOR]

---

### Post by steeldriver on 2015-08-13
I don't recommend using /root for anything, but seeing as that's what you've done let's go with that for now

What is the output of

```

ls -al

```

in the /root directory?

---

### Post by pauljw on 2015-08-13
> **VonAntero said:**
> Thanks for the quick reply guys.


It's a dedicated server and atm it doesn't have any other users. It's a fresh install and the server provider (OVH) emails the root password that I then use to login via putty. So, if I'm not missing something, there should not be any restrictions.


That would be /root

The error code is
```
**Fatal error:** Uncaught exception 'SmartyCompilerException' with message 'Syntax Error in template "./admin/themes/default/template/photos_add_direct.tpl" on line 245 "&lt;select data-selectize=&quot;categories&quot; data-value=&quot;{$selected_category|@json_encode|escape:html}&quot;" unknown modifier "json_encode"' in /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php:665 Stack trace: #0 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_compile_private_modifier.php(132): Smarty_Internal_TemplateCompilerBase->trigger_template_error('unknown modifie...', 245) #1 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php(473): Smarty_Internal_Compile_Private_Modifier->compile(Array, Object(Smarty_Internal_SmartyTemplateCompiler), Array, NULL, NULL) #2 /var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php(257): Smarty_Internal_TemplateCompilerBase->callTagCompiler('private_modifie...', Arra in **/var/www/html/gallery/include/smarty/libs/sysplugins/smarty_internal_templatecompilerbase.php** on line **665**
```

These are the threads:
[http://piwigo.org/forum/viewtopic.php?id=24853](http://piwigo.org/forum/viewtopic.php?id=24853) (team member redirects the op to the next thread)
[http://piwigo.org/forum/viewtopic.php?id=24852](http://piwigo.org/forum/viewtopic.php?id=24852) (team member suggests to delete the _data/template_c directory)

Notice the period at the beginning of the path in the error, that indicates a hidden file, use the "ls -a" command and you should see any hidden files and directories.

---

### Post by steeldriver on 2015-08-13
@pauljw a period at the beginning of the *path* just indicates that it's a relative path (i.e. relative to the current directory) - for a file to be hidden, the actual filename portion needs to start with a period

However I agree with running `ls -a` in this instance

---

### Post by VonAntero on 2015-08-13
this is what ls -al brings up
```

total 48
drwx------  5 root root 4096 Aug  8 15:36 .
drwxr-xr-x 22 root root 4096 Aug  8 15:14 ..
-rw-------  1 root root 1192 Aug 10 00:59 .bash_history
-rw-r--r--  1 root root 3106 Feb 20  2014 .bashrc
drwx------  2 root root 4096 Aug  8 15:11 .cache
-rw-r--r--  1 root root   28 Aug  8 15:11 .email
-rw-r--r--  1 root root    7 Aug  8 15:11 .mdg
-rw-------  1 root root   97 Aug  8 15:36 .mysql_history
-rw-r--r--  1 root root  326 Aug  8 15:07 .ovhrc
drwxr-xr-x  2 root root 4096 Aug  8 15:26 piwigo-screen
-rw-r--r--  1 root root  140 Feb 20  2014 .profile
drwxr-xr-x  2 root root 4096 Aug  8 15:15 .ssh
```

---

### Post by VonAntero on 2015-08-13
Got it!
Took a while to get the hang of it all, but thanks to all the help I was able to navigate my way to the right place and delete the directory.

I needed to get out of the /root and then follow the path in the error code "[COLOR=#000000][FONT=Times New Roman]/var/www/html/gallery/...".
[/FONT][/COLOR]There I could find the _data/template_c directory, thanks to the ls **-a** command.
After deleting it, I rebooted the server and now it works!
Hooray!

Thank you all for the tips!

---

