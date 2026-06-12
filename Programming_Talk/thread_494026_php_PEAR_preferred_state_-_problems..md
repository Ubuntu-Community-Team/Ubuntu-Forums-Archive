---
title: "php: PEAR preferred_state - problems."
date: 2007-07-06
forum: Programming Talk
---

### Post by jingo811 on 2007-07-06
I'm a newbie when it comes to setting up and using PEAR.  Right now I'm trying to install HTML_Quickform2 but it seems like I need to lower the preferred state from "stable" down to "alpha".
That's where my problems lies.  I can't configurate the setting by using the preferred_state function can you help me?

```
mike@sanka:~$ **sudo pear install HTML_Quickform2**
Password:
[COLOR="Red"]Failed to download pear/HTML_Quickform2 within preferred state "stable", latest release is version 0.1.0, stability "alpha", use "channel://pear.php.net/HTML_Quickform2-0.1.0" to install
Cannot initialize 'channel://pear.php.net/HTML_Quickform2', invalid or missing package file[/COLOR]
Package "channel://pear.php.net/HTML_Quickform2" is not valid
install failed
mike@sanka:~$
```

The guide I'm kind of following whenever it allows to.
[http://www.sitepoint.com/article/getting-started-with-pear/3](http://www.sitepoint.com/article/getting-started-with-pear/3)

```
mike@sanka:~$ **pear config-help preferred_state**

Config help for preferred_state
===============================
Name            Type Description
preferred_state set  the installer will prefer releases
                     with this state when installing
                     packages without a version or
                     state specified
                     Valid set: stable beta alpha devel
                     snapshot

mike@sanka:~$ **pear set preferred_state**
Command 'set' is not valid, try 'pear help'
mike@sanka:~$ **pear alpha preferred_state**
Command 'alpha' is not valid, try 'pear help'
mike@sanka:~$ **pear set preferred_state alpha**
Command 'set' is not valid, try 'pear help'
mike@sanka:~$ **pear preferred_state alpha**
Command 'preferred_state' is not valid, try 'pear help'
mike@sanka:~$ **pear preferred_state set alpha**
Command 'preferred_state' is not valid, try 'pear help'
mike@sanka:~$
mike@sanka:~$ **pear config set preferred_state alpha**
Command 'config' is not valid, try 'pear help'
mike@sanka:~$ **pear config set preferred_state set**
Command 'config' is not valid, try 'pear help'
mike@sanka:~$ **pear set preferred_state set**
Command 'set' is not valid, try 'pear help'
mike@sanka:~$



```

---

### Post by bclark on 2007-07-06
pear config-set preferred_state alpha

---

### Post by bclark on 2007-07-06
oh and when you install something use:

pear -v install -a <class name> 

that will grab the deps for you

and for help use:

pear help

---

### Post by jingo811 on 2007-07-06
Tnx for your help!  Could you also explain what the **-v** and **-a** does?  Also could you take a look at my terminal and see if things looks ok?
> 
mike@sanka:~$ **sudo pear -v install -a HTML_Quickform**
[COLOR="Red"]WARNING: "pear/HTML_QuickForm" is deprecated in favor of "pear/HTML_QuickForm2"
WARNING: "pear/HTML_Common" is deprecated in favor of "pear/HTML_Common2"[/COLOR]
[B]downloading HTML_QuickForm-3.2.9.tgz ...
Starting to download HTML_QuickForm-3.2.9.tgz (101,392 bytes)
..................done: 101,392 bytes
downloading HTML_Common-1.2.4.tgz ...
Starting to download HTML_Common-1.2.4.tgz (4,519 bytes)
...done: 4,519 bytes[/B]
+ create dir /usr/share/pear/HTML
md5sum ok: /usr/share/pear/HTML/Common.php
about to commit 4 file operations
successfully committed 4 file operations
install ok: channel://pear.php.net/HTML_Common-1.2.4
+ create dir /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/styles
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/styles/f ancygroup.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/styles/g reen.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/flexy-dy namic.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/flexy-st atic.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/html.htm l
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/it-dynam ic-2.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/it-dynam ic.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/it-stati c.html
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/label.ht ml
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/smarty-d ynamic-fancygroup.tpl
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/smarty-d ynamic-green.tpl
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/smarty-d ynamic.tpl
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/templates/smarty-s tatic.tpl
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/FlexyDynamic_examp le.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/FlexyStatic_exampl e.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/ITDynamic_example. php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/ITDynamic_example2 .php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/ITStatic_example.p hp
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/multiple-labels.ph p
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/QuickHtml_example. php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/SmartyDynamic_exam ple.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/renderers/SmartyStatic_examp le.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/elements.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/filters.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/formrule.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/groups.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/rules-builtin.php
md5sum ok: /usr/share/pear/docs/HTML_QuickForm/docs/rules-custom.php
+ create dir /usr/share/pear/HTML/QuickForm/Renderer
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/Array.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/ArraySmarty.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/Default.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/ITDynamic.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/ITStatic.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/Object.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/ObjectFlexy.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer/QuickHtml.php
+ create dir /usr/share/pear/HTML/QuickForm/Rule
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Callback.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Compare.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Email.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Range.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Regex.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule/Required.php
md5sum ok: /usr/share/pear/HTML/QuickForm/advcheckbox.php
md5sum ok: /usr/share/pear/HTML/QuickForm/autocomplete.php
md5sum ok: /usr/share/pear/HTML/QuickForm/button.php
md5sum ok: /usr/share/pear/HTML/QuickForm/checkbox.php
md5sum ok: /usr/share/pear/HTML/QuickForm/date.php
md5sum ok: /usr/share/pear/HTML/QuickForm/element.php
md5sum ok: /usr/share/pear/HTML/QuickForm/file.php
md5sum ok: /usr/share/pear/HTML/QuickForm/group.php
md5sum ok: /usr/share/pear/HTML/QuickForm/header.php
md5sum ok: /usr/share/pear/HTML/QuickForm/hidden.php
md5sum ok: /usr/share/pear/HTML/QuickForm/hiddenselect.php
md5sum ok: /usr/share/pear/HTML/QuickForm/hierselect.php
md5sum ok: /usr/share/pear/HTML/QuickForm/html.php
md5sum ok: /usr/share/pear/HTML/QuickForm/image.php
md5sum ok: /usr/share/pear/HTML/QuickForm/input.php
md5sum ok: /usr/share/pear/HTML/QuickForm/link.php
md5sum ok: /usr/share/pear/HTML/QuickForm/password.php
md5sum ok: /usr/share/pear/HTML/QuickForm/radio.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Renderer.php
md5sum ok: /usr/share/pear/HTML/QuickForm/reset.php
md5sum ok: /usr/share/pear/HTML/QuickForm/Rule.php
md5sum ok: /usr/share/pear/HTML/QuickForm/RuleRegistry.php
md5sum ok: /usr/share/pear/HTML/QuickForm/select.php
md5sum ok: /usr/share/pear/HTML/QuickForm/static.php
md5sum ok: /usr/share/pear/HTML/QuickForm/submit.php
md5sum ok: /usr/share/pear/HTML/QuickForm/text.php
md5sum ok: /usr/share/pear/HTML/QuickForm/textarea.php
md5sum ok: /usr/share/pear/HTML/QuickForm/xbutton.php
md5sum ok: /usr/share/pear/HTML/QuickForm.php
[B]about to commit 216 file operations
successfully committed 216 file operations
install ok: channel://pear.php.net/HTML_QuickForm-3.2.9[/B]
mike@sanka:~$

---

### Post by bclark on 2007-07-07
no problem!

-v gives a verbose output
-a gets all the other required pear packages as well

it looks like everything went ok on your end, however if you are writing a new app and using QuickForm and Common, you may want to go ahead and get QuickForm2 and Common2, as it looks like the originals will no longer be developed.

you can also do 'sudo pear -v upgrade-all' to make sure all your packages are up to date.

---

### Post by jingo811 on 2007-07-07
tnx :p

---

