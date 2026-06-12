---
title: "Scite Bash definitions"
date: 2007-03-23
forum: Programming Talk
---

### Post by lakersforce on 2007-03-23
Where can I find a [COLOR="Orange"]definition ([/COLOR][COLOR="Yellow"]language[/COLOR][COLOR="Orange"])[/COLOR] file of [COLOR="Blue"]bash scripting[/COLOR] for use in the [COLOR="Red"]scite[/COLOR] editor?

---

### Post by pmasiar on 2007-03-23
1) [http://www.google.com/search?q=bash+scite](http://www.google.com/search?q=bash+scite) : Same file as Perl

2) Are you trying to be cute with colors, lakersforce? Please don't

EDIT: I did not beat you, SuSUntu - your help is more helpfull than mine :-)

---

### Post by SuSUntu on 2007-03-23
Do you dislike the built-in language template?

The **perl.properties** file contains the bash related settings. If you take a look at the header information in the file you'll see this:

```

# Define SciTE settings for Perl and Bash files.

file.patterns.perl=*.pl;*.pm;*.cgi;*.pod
file.patterns.bash=*.sh;*.bsh;configure

shbang.perl=pl
shbang.sh=sh

filter.perl=Perl (pl pm)|$(file.patterns.perl)|
filter.bash=Bash (sh bsh)|$(file.patterns.bash)|

lexer.$(file.patterns.perl)=perl
lexer.$(file.patterns.bash)=bash

```

Just select "Perl" from SciTE's Language menu. Also, I'm pretty sure that selecting "Shell" under the Language menu invokes the same **perl.properties** file as a) the results seem to be identical and b) there is no **shell.properties** file.

If you still find this lacking, you can edit the **perl.properties** file or you can try the **bash.properties** file posted here:

[http://scite-tools.googlecode.com/svn/](http://scite-tools.googlecode.com/svn/)

However, I doubt you'll find any differences in functionality using the built-in **perl.properties** file and the **bash.properties** file as it appears to me that the latter is simply the former with the Perl stuff cut out.

If you go ahead and try the **bash.properties** file, be sure to add it to the appropriate sections in the **SciTEGlobal.properties** file.


EDIT:

Sorry, guys. Pmasiar beat me to it.

---

### Post by lakersforce on 2007-03-24
> **SuSUntu said:**
> 
If you go ahead and try the **bash.properties** file, be sure to add it to the appropriate sections in the **SciTEGlobal.properties** file.


And what would the appropriate edit be?

---

### Post by SuSUntu on 2007-03-24
Place the bash properties file in the directory:

/usr/share/scite

and name it something appropriate (e.g., bash.properties or mybash.properties). The portion of the name before the '.' is at your discretion; the '.properties' part of the name is standard.

**To add the item to the Scite 'Language' menu:**

Under section, **# Define the Lexer menu**, of the **SciTEGlobal.properties** file, add:

```

MyBash|bsh||\

```

where MyBash is the portion of the name of the properties file to the left of the '.' (e.g., 'Bash' for  bash.properties or 'MyBash' for mybash.properties, whatever you have named it; capitalization is at your discretion ... it just depends on how you want it to appear in the menu).

**To add the item to the Scite 'Options > Edit Properties"' menu:**

Under section, **# Import all the language specific properties files**, of the **SciTEGlobal.properties** file, add:

```

import mybash

```

where 'mybash' is the portion of the name of the properties file to the left of the '.' (e.g., 'bash' for bash.properties or 'mybash' for mybash.properties, whatever you have named it).

---

