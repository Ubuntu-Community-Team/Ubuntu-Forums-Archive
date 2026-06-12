---
title: "Scite - Default Open All Files"
date: 2007-01-07
forum: Programming Talk
---

### Post by indytim on 2007-01-07
I'm running Scite for my editor-of-choice.  One irritant that I haven't been able to crack yet is on the open file window within Scite.  I would like to have it default open to "All Files" vs "All Sources".  I haven't found the coding required to modify the options file.  Any suggestions?

Thanks,

IndyTim

---

### Post by HadroLepton on 2007-01-07
i have been trying that too.

this line should work, but it doesn't. i don't know why
```
open.filter=all files (*)|*|$(open.filter)
```

well actually it does work, but then you can't choose any other filter because it will only have "all files" to choose from.

---

### Post by Javahype on 2007-02-10
I did the following to set SciTE's Open dialog box filter to "All Files (*)". I'm assuming the original posters most likely know a lot about Ubuntu at this point; the extra details are for new Ubuntu users who come across this.

[LIST=1]
[*]Open a terminal window. For anyone new to Ubuntu: go to the Main Menu (usually in the top left corner of your screen) and then select **Applications > Accessories > Terminal**.
[*]Once in the Terminal window, type "**sudo scite**", without the quotes, so that you run SciTE as a superuser. You will most likely be prompted for a Password (usually the root password); type it in. Running SciTE as a superuser gives you the required permission to modify the properties file specified in the next step.
[*]Now, you should have SciTE running. On SciTE's menu bar, go to **Options > Open User Options File.** This should open the file called **.SciTEUser.properties** . If you've never made changes to this file, the file should be empty.
[*]In this file, please **type (or copy-and-paste) all of the following code**. It's a little long, but necessary to ensure all of the default filters are listed, too:

```

# Open Filter
if PLAT_GTK
	all.files=All Files (*)|*|Hidden Files (.*)|.*|
open.filter=\
$(all.files)\
All Source|$(source.files)\
$(filter.ada)\
$(filter.conf)\
$(filter.asm)\
$(filter.asn1)\
$(filter.ave)\
$(filter.baan)\
$(filter.bash)\
$(filter.caml)\
$(filter.cpp)\
#$(filter.ch)\
$(filter.css)\
$(filter.eiffel)\
$(filter.erlang)\
$(filter.fortran)\
$(filter.idl)\
$(filter.inno)\
$(filter.java)\
$(filter.js)\
$(filter.kix)\
$(filter.lout)\
$(filter.lua)\
$(filter.matlab)\
$(filter.metapost)\
$(filter.mmixal)\
$(filter.nncrontab)\
$(filter.nsis)\
$(filter.opal)\
$(filter.pascal)\
$(filter.perl)\
$(filter.php)\
$(filter.pov)\
$(filter.prg)\
$(filter.properties)\
$(filter.ps)\
$(filter.python)\
$(filter.ruby)\
$(filter.sql)\
$(filter.specman)\
$(filter.tcl)\
$(filter.tex)\
$(filter.text)\
$(filter.vb)\
$(filter.web)\
$(filter.yaml)\
$(filter.verilog)\
$(filter.vhdl)

```

[*]Once you've completed Step 4, **save your changes**. To see if the change occurred correctly, bring up the Open dialog by going to **File > Open**. Instead of "All Sources", you should now see "All Files (*)" as the default filter.
[*]Once you're satisfied with the changes, please close SciTE down completely. This ensures that you end this instance of SciTE being run as a superuser. Then, just run SciTE as you normally would.
[/LIST]

Hope this helps.
- Javahype

---

### Post by indytim on 2007-02-11
Thanks much, worked great.  Opinion-> this should be baked in as the default for Scite.

IndyTim

---

### Post by HadroLepton on 2007-08-10
bumping ancient thread. i have been doing some research into this issue and found this thread again.

here is a hack which works and you don't need to sudo. add this line to your **~/.SciTEUser.properties** file
```

source.files=*

```

it is a hack because now **every** file is a "source file".

another way is to copy the definition of **open.filter** from **/usr/share/scite/SciTEGlobal.properties** and redefine the entire thing but switch the position of **$(source.files)** and **$(all.files)**. this is what Javahype suggested but i do not understand why you need sudo for that, unless Javahype meant to edit **/usr/share/scite/SciTEGlobal.properties** instead of **~/.SciTEUser.properties**.

only for those interested in some details:
my previous solution does not work because scite is doing a lazy evaluation. that means the values of the variables are evaluated at the time where it is needed, instead of the time where it is defined.

for example
```

var1=foo
var2=$(var1)
var1=bar

```

evaluates to
```

var1=bar
var2=bar

```

now to my previous solution
```

open.filter=all files (*)|*|$(open.filter)

```

evaluates to cyclic dependency. scite obviously recognizes cyclic dependencies and stops evaluating the value.

---

### Post by CParticle on 2008-04-14
I just copied the Filter section out of the global properties and flip flopped the all files and all source lines so all files is first.  I bolded it below if your in text only its the two lines after open.filter=\.  My guess is that this is the right way to do it.  It looks like the entire filter section is an all or nothing deal which is why you need to copy everything and not just those lines.  I tried commenting the rest of the line but that didn't work.  I've kept the windows stuff as I like to keep my config files flexible.  Sorry editing to say that I put this in my SciteUser.properties file.

---Begin scite config section---
source.files=*.asm;*.c;*.cc;*.cpp;*.cxx;*.cs;*.h;*.hh;*.hxx;*.hpp;\
*.idl;*.odl;*.rc;*.rc2;*.dlg;*.def;\
*.vb;*.vbs;*.bas;*.frm;*.cls;*.ctl;\
*.java;*.js;*.py;*.pl;*.rb;*.cgi;*.lua;*.conf;\
make*;*.mak;\
*.properties;*.html;*.xml;*.iface;*.bat;*.e

if PLAT_WIN
	all.files=All Files (*.*)|*.*|
if PLAT_GTK
	all.files=All Files (*)|*|Hidden Files (.*)|.*|
open.filter=\
[B]$(all.files)\
All Source|$(source.files)|\[/B]
$(filter.ada)\
$(filter.conf)\
$(filter.asm)\
$(filter.asn1)\
$(filter.ave)\
$(filter.baan)\
$(filter.bash)\
$(filter.caml)\
$(filter.cpp)\
#$(filter.ch)\
$(filter.css)\
$(filter.eiffel)\
$(filter.erlang)\
$(filter.fortran)\
$(filter.idl)\
$(filter.inno)\
$(filter.java)\
$(filter.js)\
$(filter.kix)\
$(filter.lout)\
$(filter.lua)\
$(filter.matlab)\
$(filter.metapost)\
$(filter.mmixal)\
$(filter.nncrontab)\
$(filter.nsis)\
$(filter.opal)\
$(filter.pascal)\
$(filter.perl)\
$(filter.php)\
$(filter.pov)\
$(filter.prg)\
$(filter.properties)\
$(filter.ps)\
$(filter.python)\
$(filter.ruby)\
$(filter.sql)\
$(filter.specman)\
$(filter.tcl)\
$(filter.tex)\
$(filter.text)\
$(filter.vb)\
$(filter.web)\
$(filter.yaml)\
$(filter.verilog)\
$(filter.vhdl)

---End scite config section---

---

