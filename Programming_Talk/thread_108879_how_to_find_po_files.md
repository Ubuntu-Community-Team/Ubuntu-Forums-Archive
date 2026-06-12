---
title: "how to find po files?"
date: 2005-12-27
forum: Programming Talk
---

### Post by freemanen on 2005-12-27
I would like to translate som program to swedish but i can't find how to work with po files. Is there any good description about how to do that? I dosen't know there po file is on the computer?

---

### Post by David Marrs on 2005-12-27
[Gnu Gettext](http://www.gnu.org/software/gettext/) is the app that generates .po files for different locales.

---

### Post by asimon on 2005-12-28
Usually po files are not installed on the system with the software, only the binary mo files. The mo files are generated from the po files via gettext. On Ubuntu you find most mo files under /usr/share/locale-langpack/ .

Thus to get the po files you have to get the source of the package. Usually you find them in the source under a 'po' subdirectory. You can get the source via 'apt-get source <package>' or directly from a upstream webpage/mirror/cvs.

There are several applications which make it more convenient to work with and manage po files like [kbabel](http://i18n.kde.org/tools/kbabel/) or [GTranslator](http://gtranslator.sourceforge.net/). I am sure there are plenty of others out there.

Here is the [documentation for the GNU gettext Utilities](http://www.gnu.org/software/gettext/manual/). Here is some more [information about POT and PO Files](http://i18n.kde.org/translation-howto/gui-translation.html) from the KDE translation howto.

Because this is a Ubuntu forum I highly recommend [Rosetta](https://launchpad.net/rosetta/) for translations. For more information see [Ubuntu WIKI: Rosetta](https://wiki.ubuntu.com/Rosetta) and [RosettaFAQ](https://wiki.ubuntu.com/RosettaFAQ).

---

### Post by c2tarun on 2010-10-15
are you able to do any translations in your language.
i m also trying to convert some applications of ubuntu in hindi, but unable to do so.
i need help please reply...

---

### Post by worksofcraft on 2010-10-15
> **c2tarun said:**
> are you able to do any translations in your language.
i m also trying to convert some applications of ubuntu in hindi, but unable to do so.
i need help please reply...

The first thing you must do is top get a .po file for the application.

If you have the source code you can use the xgettext tool to extract all the translatable strings. If it is a well established project then they probably have a mailing list and are eager to get help from translators in different locales.

Here is an [excellent introduction tutorial]("//oriya.sarovar.org/docs/gettext_single.html") that was everything I needed to know to making my own translations. I wrote [project exploring internationalization and localization]("http://code.google.com/p/speaknumber/") here and the html documents are full of ideas experiments and code. Full working examples are in the other files of the project.

---

### Post by c2tarun on 2010-10-16
do we have to install our language support first or we can do it directly??

---

### Post by worksofcraft on 2010-10-16
> **c2tarun said:**
> do we have to install our language support first or we can do it directly??

Since the actual translation is done manually you can prepare .po files for any lanuage without installing support for that language.
You will evidently have to be able to enter the appropriate characters somehow.
If they are not on your keyboard. You can also compile the .po file into a .mo file (the binary run time version) without installing the language support, but if you want to use it and test it you must run sudo locale-gen. Here I'll copy my notes from when I started learning that Oriya tutorial:
```

from http://oriya.sarovar.org/docs/gettext_single.html

 create internationalized version of hello.c

$> gcc -o hello hello.c

# extract translatable strings with:
$> xgettext -d hello -s -o hello.pot hello.c

The -s option tells xgettext to produce sorted output.
The message domain for the program should be specified as the argument to
the -d option, and should match the domain specified in the call to textdomain
(on line 9 of the program source)

 copy the portable object template to oriya.po using
$> msginit -l or_IN -o oriya.po -i hello.pot
# Note: -l (letter l) option defines the locale


do the translations by hand

# compile it to machine object
$> msgfmt -c -v -o hello.mo oriya.po

copy it to the location whose base directory is given by the second argument to
bindtextdomain. The final location of the file will be in the sub-directory
LL/LC_MESSAGES or LL_CC/LC_MESSAGES under the base directory, where LL stands
for a language, and CC for a country

$> sudo mkdir -p /usr/share/locale/or_IN/LC_MESSAGES
$> sudo cp hello.mo /usr/share/locale/or_IN/LC_MESSAGES

#generate the locale if it doesn't exist:
$> sudo locale-gen or_IN

#select the locale
$> export LANG=or_IN

#run the program:
$> ./hello

```

I often still refer to this to make sure I use the right commands :)

---

### Post by nvteighen on 2010-10-16
> **c2tarun said:**
> do we have to install our language support first or we can do it directly??

Code using gettext will need to know what locale is being used in order to choose the correct language file... so, yes, you need to have support for the needed language support to work correctly.

---

### Post by c2tarun on 2010-10-16
> **worksofcraft said:**
> Since the actual translation is done manually you can prepare .po files for any lanuage without installing support for that language.
You will evidently have to be able to enter the appropriate characters somehow.
If they are not on your keyboard. You can also compile the .po file into a .mo file (the binary run time version) without installing the language support, but if you want to use it and test it you must run sudo locale-gen. Here I'll copy my notes from when I started learning that Oriya tutorial:
```

from http://oriya.sarovar.org/docs/gettext_single.html

 create internationalized version of hello.c

$> gcc -o hello hello.c

# extract translatable strings with:
$> xgettext -d hello -s -o hello.pot hello.c

The -s option tells xgettext to produce sorted output.
The message domain for the program should be specified as the argument to
the -d option, and should match the domain specified in the call to textdomain
(on line 9 of the program source)

 copy the portable object template to oriya.po using
$> msginit -l or_IN -o oriya.po -i hello.pot
# Note: -l (letter l) option defines the locale


do the translations by hand

# compile it to machine object
$> msgfmt -c -v -o hello.mo oriya.po

copy it to the location whose base directory is given by the second argument to
bindtextdomain. The final location of the file will be in the sub-directory
LL/LC_MESSAGES or LL_CC/LC_MESSAGES under the base directory, where LL stands
for a language, and CC for a country

$> sudo mkdir -p /usr/share/locale/or_IN/LC_MESSAGES
$> sudo cp hello.mo /usr/share/locale/or_IN/LC_MESSAGES

#generate the locale if it doesn't exist:
$> sudo locale-gen or_IN

#select the locale
$> export LANG=or_IN

#run the program:
$> ./hello

```I often still refer to this to make sure I use the right commands :)



wow....
you tutorial is awesome, now i am able to translate some of applications to my native language. :)
but it is just one steps among several to complete my project.
still i have no idea how to convert linux ubuntu into hindi.
what i thought is dowload the source code for gnome, and change po files there.
or download the source code for gnome default window manager and make changes there.
but still its a vague idea.
can you please suggest me something.
thanx

---

### Post by worksofcraft on 2010-10-16
> **c2tarun said:**
> ...
still i have no idea how to convert linux ubuntu into hindi.
what i thought is dowload the source code for gnome, and change po files there.
or download the source code for gnome default window manager and make changes there.
but still its a vague idea.
can you please suggest me something.
thanx

When you install Linux you can select Hindi as your native language. I gave it a try in a virtual box to see what it does. You see below is the image where you select Hindi as your native language during installation and then also I include an image of it running.

As you can see it still has mostly English on the task bar and in the menus. The reason for this is because they are configurable...

... like text for the main menu is in /etc/xdg/menus/applications.menu and then there are separate .directory files in /usr/share/desktop-directories and presumably nobody has made Hindi versions of them yet :confused:

I suppose you could try editing them but I would strongly suggest you **do that in a virtual machine where you can save a "snapshot" to restore if something goes wrong**!

p.s. There are many [gnome translation teams]("http://l10n.gnome.org/teams/") active all around the world and I see there is also a [translation website for Hindi]("http://www.indlinux.org/wiki/index.php/Hindi") there. I suspect they will be pleased if you want to help them and should be able to help you get started :)

---

### Post by c2tarun on 2010-10-16
> **worksofcraft said:**
> When you install Linux you can select Hindi as your native language. I gave it a try in a virtual box to see what it does. You see below is the image where you select Hindi as your native language during installation and then also I include an image of it running.

As you can see it still has mostly English on the task bar and in the menus. The reason for this is because they are configurable...

... like text for the main menu is in /etc/xdg/menus/applications.menu and then there are separate .directory files in /usr/share/desktop-directories and presumably nobody has made Hindi versions of them yet :confused:

I suppose you could try editing them but I would strongly suggest you **do that in a virtual machine where you can save a "snapshot" to restore if something goes wrong**!

p.s. There are many [gnome translation teams]("http://l10n.gnome.org/teams/") active all around the world and I see there is also a [translation website for Hindi]("http://www.indlinux.org/wiki/index.php/Hindi") there. I suspect they will be pleased if you want to help them and should be able to help you get started :)


you are right. i tried that too and there are many names and words still in hindi.
what i was thinking is to do a raw installation on a machine with no upgrades nothing. then i'll covert the default applications provided with ubuntu (as many as possible :) can't guarantee all ).
anyway, thanx a lot for helping. now i'll do some homework.
i have a request. please keep  visiting this thread or if possible subscribe to this thread. in case i need any further guidance i'll post you.
thanx a lot

---

### Post by c2tarun on 2010-10-16
> **worksofcraft said:**
> When you install Linux you can select Hindi as your native language. I gave it a try in a virtual box to see what it does. You see below is the image where you select Hindi as your native language during installation and then also I include an image of it running.

As you can see it still has mostly English on the task bar and in the menus. The reason for this is because they are configurable...

... like text for the main menu is in /etc/xdg/menus/applications.menu and then there are separate .directory files in /usr/share/desktop-directories and presumably nobody has made Hindi versions of them yet :confused:

I suppose you could try editing them but I would strongly suggest you **do that in a virtual machine where you can save a "snapshot" to restore if something goes wrong**!

p.s. There are many [gnome translation teams]("http://l10n.gnome.org/teams/") active all around the world and I see there is also a [translation website for Hindi]("http://www.indlinux.org/wiki/index.php/Hindi") there. I suspect they will be pleased if you want to help them and should be able to help you get started :)


you are right. i tried that too and there are many names and words still in hindi.
what i was thinking is to do a raw installation on a machine with no upgrades nothing. then i'll covert the default applications provided with ubuntu (as many as possible :) can't guarantee all ).
anyway, thanx a lot for helping. now i'll do some homework.
i have a request. please keep  visiting this thread or if possible subscribe to this thread. in case i need any further guidance i'll post you.
thanx a lot

---

### Post by c2tarun on 2010-10-17
hey can you please tell me how to get the source code of a particular software in hindi and english.
it'll be good to take a look at them
thanx

---

### Post by worksofcraft on 2010-10-17
> **c2tarun said:**
> hey can you please tell me how to get the source code of a particular software in hindi and english.
it'll be good to take a look at them
thanx

I think practically all the programming languages are based on English keywords. The only difference you may find is that the input and output strings embedded in the program source are in a different language.

However that is often not so wise because it fails spectacularly when the end user doesn't have the same ISO character set loaded :shock:

Luckily all the utf-8 locales are mutually compatible so hopefully all those old code pages will soon be deprecated. I posted somewhere else how when you program non-ascii text in your source code [programming languages like Python simply won't let them be translated]("http://ubuntuforums.org/showthread.php?p=9955792#post9955792") :confused: I have no idea why because gettext can handle it just fine :) 

Something that may be useful is the msgunfmt tool... it lets you look at the translations in the installed .mo files.
I don't have Hindi installed at the moment, but if go to my /usr/share/locale/zh_CN/LC_MESSAGES (Chinese) folder I find a bunch of .mo files and here is some sample output:
```

/usr/share/locale/zh_CN/LC_MESSAGES$> msgunfmt naut*
msgid ""
msgstr ""
"Project-Id-Version: nautilus-open-terminal\n"
"Report-Msgid-Bugs-To: http://bugzilla.gnome.org/enter_bug.cgi?"
"product=nautilus-open-terminal&component=general\n"
"POT-Creation-Date: 2009-03-19 02:16+0000\n"
"PO-Revision-Date: 2009-03-28 11:19+0800\n"
"Last-Translator: Zhang Miao <mymzhang@gmail.com>\n"
"Language-Team: zh_CN <i18n-translation@lists.linux.net.cn>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

msgid ""
"If set to true, and if the terminal file manager \"Midnight Commander\" is "
"installed, then an \"Open in Midnight Commander\" menu item will be "
"displayed in the context menu."
msgstr ""
"&#33509;&#35774;&#20026;&#30495;&#65292;&#24182;&#19988;&#22914;&#26524;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120;&#8220;Midnight Commander&#8221;&#24050;&#23433;&#35013;&#65292;&#22312;&#30446;&#24405;&#33756;&#21333;&#20013;&#20250;&#26174;"
"&#31034;&#8220;&#22312; Midnight Commander &#20013;&#25171;&#24320;&#8221;&#33756;&#21333;&#39033;&#12290;"

msgid ""
"If set to true, then opening a terminal on the desktop will open a terminal "
"in the home directory. Otherwise, it will be opened in the desktop "
"directory. Note that this key is irrelevant if the desktop directory is "
"identical to the home directory."
msgstr ""
"&#22914;&#26524;&#35774;&#20026;&#30495;&#65292;&#22312;&#26700;&#38754;&#19978;&#25171;&#24320;&#32456;&#31471;&#23558;&#20250;&#35774;&#20026;&#25171;&#24320;&#22312;&#20027;&#30446;&#24405;&#12290;&#21542;&#21017;&#65292;&#23427;&#23558;&#20250;&#34987;&#25171;&#24320;&#22312; &#26700;&#38754;&#30446;"
"&#24405;&#12290;&#27880;&#24847;&#27492;&#38190;&#36319;&#26700;&#38754;&#30446;&#24405;&#26159;&#21542;&#21516;&#20110;&#20027;&#30446;&#24405;&#19981;&#30456;&#20851;&#12290;"

msgid "Open T_erminal"
msgstr "&#25171;&#24320;&#32456;&#31471;(_E)"

msgid "Open _Midnight Commander"
msgstr "&#25171;&#24320; _Midnight Commander"

msgid "Open a terminal"
msgstr "&#25171;&#24320;&#32456;&#31471;"

msgid "Open in T_erminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;(_E)"

msgid "Open in _Local Terminal"
msgstr "&#22312;&#26412;&#22320;&#32456;&#31471;&#20013;&#25171;&#24320;(_L)"

msgid "Open in _Midnight Commander"
msgstr "&#22312; _Midnight Commander &#20013;&#25171;&#24320;"

msgid "Open in _Remote Terminal"
msgstr "&#22312;&#36828;&#31243;&#32456;&#31471;&#20013;&#25171;&#24320;(_R)"

msgid "Open the currently open folder in a terminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;&#24403;&#21069;&#25991;&#20214;&#22841;"

msgid ""
"Open the currently open folder in the terminal file manager Midnight "
"Commander"
msgstr "&#22312;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander &#20013;&#25171;&#24320;&#24403;&#21069;&#25171;&#24320;&#30340;&#25991;&#20214;&#22841;"

msgid "Open the currently selected folder in a terminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;&#30446;&#21069;&#36873;&#20013;&#30340;&#25991;&#20214;&#22841;"

msgid ""
"Open the currently selected folder in the terminal file manager Midnight "
"Commander"
msgstr "&#22312;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander &#20013;&#25171;&#24320;&#30446;&#21069;&#36873;&#20013;&#30340;&#25991;&#20214;&#22841;"

msgid "Open the terminal file manager Midnight Commander"
msgstr "&#25171;&#24320;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander"

msgid "Whether a Midnight Commander menu item should be displayed"
msgstr "Midnight Commander &#39033;&#30446;&#33756;&#21333;&#26159;&#21542;&#34987;&#26174;&#31034;"

msgid ""
"Whether opening a terminal on the desktop opens a terminal in the home "
"directory"
msgstr "&#22312;&#26700;&#38754;&#19978;&#25171;&#24320;&#32456;&#31471;&#26102;&#26159;&#21542;&#35774;&#32622;&#20026;&#25171;&#24320;&#22312;&#20027;&#30446;&#24405;"

```

I can't actually read any Chinese, but I installed to test my [numeric output localization routines]("http://code.google.com/p/speaknumber/").

p.s. **now say there was no Hindi translation available for the above domain, then you could take the Chinese one and insert your translations where the Chinese is. You might want to modify the translation team and contact details too and then reformat at as a new .mo file using msgfmt**.

---

### Post by c2tarun on 2010-10-17
> **worksofcraft said:**
> I think practically all the programming languages are based on English keywords. The only difference you may find is that the input and output strings embedded in the program source are in a different language.

However that is often not so wise because it fails spectacularly when the end user doesn't have the same ISO character set loaded :shock:

Luckily all the utf-8 locales are mutually compatible so hopefully all those old code pages will soon be deprecated. I posted somewhere else how when you program non-ascii text in your source code [programming languages like Python simply won't let them be translated]("http://ubuntuforums.org/showthread.php?p=9955792#post9955792") :confused: I have no idea why because gettext can handle it just fine :) 

Something that may be useful is the msgunfmt tool... it lets you look at the translations in the installed .mo files.
I don't have Hindi installed at the moment, but if go to my /usr/share/locale/zh_CN/LC_MESSAGES (Chinese) folder I find a bunch of .mo files and here is some sample output:
```

/usr/share/locale/zh_CN/LC_MESSAGES$> msgunfmt naut*
msgid ""
msgstr ""
"Project-Id-Version: nautilus-open-terminal\n"
"Report-Msgid-Bugs-To: http://bugzilla.gnome.org/enter_bug.cgi?"
"product=nautilus-open-terminal&component=general\n"
"POT-Creation-Date: 2009-03-19 02:16+0000\n"
"PO-Revision-Date: 2009-03-28 11:19+0800\n"
"Last-Translator: Zhang Miao <mymzhang@gmail.com>\n"
"Language-Team: zh_CN <i18n-translation@lists.linux.net.cn>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=utf-8\n"
"Content-Transfer-Encoding: 8bit\n"

msgid ""
"If set to true, and if the terminal file manager \"Midnight Commander\" is "
"installed, then an \"Open in Midnight Commander\" menu item will be "
"displayed in the context menu."
msgstr ""
"&#33509;&#35774;&#20026;&#30495;&#65292;&#24182;&#19988;&#22914;&#26524;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120;“Midnight Commander”&#24050;&#23433;&#35013;&#65292;&#22312;&#30446;&#24405;&#33756;&#21333;&#20013;&#20250;&#26174;"
"&#31034;“&#22312; Midnight Commander &#20013;&#25171;&#24320;”&#33756;&#21333;&#39033;&#12290;"

msgid ""
"If set to true, then opening a terminal on the desktop will open a terminal "
"in the home directory. Otherwise, it will be opened in the desktop "
"directory. Note that this key is irrelevant if the desktop directory is "
"identical to the home directory."
msgstr ""
"&#22914;&#26524;&#35774;&#20026;&#30495;&#65292;&#22312;&#26700;&#38754;&#19978;&#25171;&#24320;&#32456;&#31471;&#23558;&#20250;&#35774;&#20026;&#25171;&#24320;&#22312;&#20027;&#30446;&#24405;&#12290;&#21542;&#21017;&#65292;&#23427;&#23558;&#20250;&#34987;&#25171;&#24320;&#22312; &#26700;&#38754;&#30446;"
"&#24405;&#12290;&#27880;&#24847;&#27492;&#38190;&#36319;&#26700;&#38754;&#30446;&#24405;&#26159;&#21542;&#21516;&#20110;&#20027;&#30446;&#24405;&#19981;&#30456;&#20851;&#12290;"

msgid "Open T_erminal"
msgstr "&#25171;&#24320;&#32456;&#31471;(_E)"

msgid "Open _Midnight Commander"
msgstr "&#25171;&#24320; _Midnight Commander"

msgid "Open a terminal"
msgstr "&#25171;&#24320;&#32456;&#31471;"

msgid "Open in T_erminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;(_E)"

msgid "Open in _Local Terminal"
msgstr "&#22312;&#26412;&#22320;&#32456;&#31471;&#20013;&#25171;&#24320;(_L)"

msgid "Open in _Midnight Commander"
msgstr "&#22312; _Midnight Commander &#20013;&#25171;&#24320;"

msgid "Open in _Remote Terminal"
msgstr "&#22312;&#36828;&#31243;&#32456;&#31471;&#20013;&#25171;&#24320;(_R)"

msgid "Open the currently open folder in a terminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;&#24403;&#21069;&#25991;&#20214;&#22841;"

msgid ""
"Open the currently open folder in the terminal file manager Midnight "
"Commander"
msgstr "&#22312;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander &#20013;&#25171;&#24320;&#24403;&#21069;&#25171;&#24320;&#30340;&#25991;&#20214;&#22841;"

msgid "Open the currently selected folder in a terminal"
msgstr "&#22312;&#32456;&#31471;&#20013;&#25171;&#24320;&#30446;&#21069;&#36873;&#20013;&#30340;&#25991;&#20214;&#22841;"

msgid ""
"Open the currently selected folder in the terminal file manager Midnight "
"Commander"
msgstr "&#22312;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander &#20013;&#25171;&#24320;&#30446;&#21069;&#36873;&#20013;&#30340;&#25991;&#20214;&#22841;"

msgid "Open the terminal file manager Midnight Commander"
msgstr "&#25171;&#24320;&#32456;&#31471;&#25991;&#20214;&#31649;&#29702;&#22120; Midnight Commander"

msgid "Whether a Midnight Commander menu item should be displayed"
msgstr "Midnight Commander &#39033;&#30446;&#33756;&#21333;&#26159;&#21542;&#34987;&#26174;&#31034;"

msgid ""
"Whether opening a terminal on the desktop opens a terminal in the home "
"directory"
msgstr "&#22312;&#26700;&#38754;&#19978;&#25171;&#24320;&#32456;&#31471;&#26102;&#26159;&#21542;&#35774;&#32622;&#20026;&#25171;&#24320;&#22312;&#20027;&#30446;&#24405;"

```I can't actually read any Chinese, but I installed to test my [numeric output localization routines]("http://code.google.com/p/speaknumber/").



hey this tool looks awesome and something i have been looking for.
can you please tell me how to install this tool.
i tried sudo apt-get install msgunfmt
but it couldn't find the package.

---

### Post by worksofcraft on 2010-10-17
> **c2tarun said:**
> hey this tool looks awesome and something i have been looking for.
can you please tell me how to install this tool.
i tried sudo apt-get install msgunfmt
but it couldn't find the package.

It is part of the gettext package and should be installed already :) type "msgunfmt --help" at command prompt!

---

### Post by c2tarun on 2010-10-17
> **worksofcraft said:**
> It is part of the gettext package and should be installed already :) type "msgunfmt --help" at command prompt!


i want to do some translations in some applications and create a debian package.
so that when i install using those packages i can get full hindi support with those softwares.
i know how to create packages using pbuilder, but i dont think that simply by creating po file saving it to po folder in source code and creating a package will do what i want.

plus can you please explain me the following line. what are these parameters?? are they some predefined variables of something else.
bindtextdomain (GETTEXT_PACKAGE, PACKAGE_LOCALE_DIR);

thanx

---

### Post by worksofcraft on 2010-10-17
> **c2tarun said:**
> i want to do some translations in some applications and create a debian package.
so that when i install using those packages i can get full hindi support with those softwares.
i know how to create packages using pbuilder, but i dont think that simply by creating po file saving it to po folder in source code and creating a package will do what i want.

plus can you please explain me the following line. what are these parameters?? are they some predefined variables of something else.
bindtextdomain (GETTEXT_PACKAGE, PACKAGE_LOCALE_DIR);

thanx
Well you are ahead of me on pbuilder and .deb packages.
however I can explain the bindtextdomain:
[php]
int main(int argc, char **argv) {
	setlocale( LC_ALL, "" );
	bindtextdomain( "hello", "/usr/share/locale" );
	textdomain( "hello" );
[/php]
First, your locale (that is language and country) is determined by setlocale based on various environment variables that the user sets. I'm not sure when one would want to specify anything other than the parameters given above.

Then bindtextdomain is telling the gettext runtime system that the translations for the domain named "hello" are to be found in the directory tree of "/usr/share/locale". They get installed in sub directory that are dedicated to the different locales.

Finally the textdomain call actually selects this is your default domain... i.e. the one that it will use to translate strings when you don't specify a different domain.

Now if you run your program with strace you can see it searching for your .mo file. If you made a program called hello then try:
```

strace ./hello
...
open("/usr/share/locale/en_NZ/LC_MESSAGES/hello.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/hello.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/hello.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/hello.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
...

```

as you can see on my system it failed to find hello.mo in any of the recommended places because I didn't install one for my locale (en_NZ = English for New Zealand).

Installing translations is as simple as copying the .mo file into the right directory :)

---

### Post by nvteighen on 2010-10-17
> **worksofcraft said:**
> When you install Linux you can select Hindi as your native language. I gave it a try in a virtual box to see what it does. You see below is the image where you select Hindi as your native language during installation and then also I include an image of it running.


It's far much easier than that... install the locale (language-support-<lang_code>) using the repositories and set the desired language at the GDM login screen...


> **c2tarun said:**
> wow....
you tutorial is awesome, now i am able to translate some of applications to my native language. :)
but it is just one steps among several to complete my project.
still i have no idea how to convert linux ubuntu into hindi.
what i thought is dowload the source code for gnome, and change po files there.
or download the source code for gnome default window manager and make changes there.
but still its a vague idea.
can you please suggest me something.
thanx

GNOME is not a program, it's a collection of programs. You have to translate every single application in it separately... That's why Ubuntu uses the Launchpad translation system (which I suggested to look at in another thread)...

From your posts I see this is some college project or similar, is it not? If so, I believe it's a bad idea for a project... It would be much more realistic if you focused on translating a big but specific application, for example, OpenOffice.org or Firefox/Iceweasel/<however is the Mozilla browser now called in Ubuntu>. Of course the choice is yours.

But, if it's just a personal project for contributing to Ubuntu, then, the best is that you translate via Launchpad's web interface. I've done it in the past and they've accepted some translations I've done for package descriptions in the Spanish localization. They desperately need people to translate stuff and will be glad to have your contribution.

---

### Post by c2tarun on 2010-10-29
thanks to worksofcraft

now i am successfully able to convert some applications in hindi.
but still i want to convert menus in gnome and system menus in hindi.. can anyone please tell me how to get the mo or po files for them...
thanx

---

### Post by worksofcraft on 2010-10-29
> **c2tarun said:**
> thanks to worksofcraft

now i am successfully able to convert some applications in hindi.
but still i want to convert menus in gnome and system menus in hindi.. can anyone please tell me how to get the mo or po files for them...
thanx

As far as I know, the various menus used by Gnome are all in text form. I do not think there are any .po/mo files being used for them because they do not contain any keywords but perhaps you can edit them directly. Do be careful though because it may stop your desktop from working and that is why I recommended using a virtual machine before.

Before you do that you should check under...
System->Administrtaion->Language Support
This is available on your launcher bar

The files I know of are:
/etc/xdg/menus/applications.menu
/usr/share/desktop-directories/
/usr/share/applications/

The Gnome desktop is quite a complex system and I haven't learnt much about it yet. You might have to google about gnome setup, customization and also look at the [linux from sratch]("http://www.linuxfromscratch.org/blfs/view/cvs/index.html") sites.

Good luck... and come back and post about what you find :)

---

### Post by c2tarun on 2010-10-29
> **worksofcraft said:**
> As far as I know, the various menus used by Gnome are all in text form. I do not think there are any .po/mo files being used for them because they do not contain any keywords but perhaps you can edit them directly. Do be careful though because it may stop your desktop from working and that is why I recommended using a virtual machine before.

Before you do that you should check under...
System->Administrtaion->Language Support
This is available on your launcher bar

The files I know of are:
/etc/xdg/menus/applications.menu
/usr/share/desktop-directories/
/usr/share/applications/

The Gnome desktop is quite a complex system and I haven't learnt much about it yet. You might have to google about gnome setup, customization and also look at the [linux from sratch]("http://www.linuxfromscratch.org/blfs/view/cvs/index.html") sites.

Good luck... and come back and post about what you find :)


thanx, i'll proceed now and reply about any progress ASAP

---

