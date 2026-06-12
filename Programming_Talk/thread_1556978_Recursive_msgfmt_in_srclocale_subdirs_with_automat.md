---
title: "Recursive msgfmt in src/locale/ subdirs with automatic translation_domain naming"
date: 2010-08-20
forum: Programming Talk
---

### Post by Interruptor on 2010-08-20
So I'm making test i18n project on pygtk.Builder and was really surprised that process of converting *.po* files to *.mo* is completely manual.
I think *msgfmt* has to have *-r* option for recursive and something like *--textdomain* for automatic *.mo* renaming.
Maybe I just can't find the right package or script?
Are there any instruments for automatic .mo creation? *locale/* directory structure is:
> ./uk/LC_MESSAGES/codin.po
./C/LC_MESSAGES/codin.pot
./ru/LC_MESSAGES/codin.po
./en/LC_MESSAGES/codin.po

Writing a script with *find -type f* myself...

---

### Post by Interruptor on 2010-08-20
code to run in directory, named as project:
**[COLOR="Red"]Attention! See improved version in next reply.[/COLOR]**
```
textdomain=`basename "$(pwd)"`
localedir=`pwd`"/locale/"

for file in `find $localedir -type f -name "*.po"`; do 
	cd $localedir
	echo "cd " "$( readlink -f "$( dirname "$file" )" )" && \
	cd "$( readlink -f "$( dirname "$file" )" )"

	echo "msgfmt -o $textdomain.mo `basename $file`" && \
	msgfmt -o $textdomain.mo `basename $file`
	#TODO: for existing .mo - revise only older than .po
done
```

---

### Post by Interruptor on 2010-08-20
Improved version for **fully-automatic** updating:
```
textdomain=`basename "$(**pwd**)"`
**localedir**=`**pwd**`"/locale/"
poeditor="virtaal"

#**mv** $localedir"C/LC_MESSAGES/"$textdomain"**.pot** $localedir"C/LC_MESSAGES/"$textdomain"`**date '+%y%m%d_%H%M'`.pot**
xgettext --sort-output --keyword=translatable -o $localedir"C/LC_MESSAGES/"$textdomain".pot" $textdomain.glade

for file in `**find** $localedir -type f -name "***.po**"`; do 
	cd $localedir
	[COLOR="Silver"]echo "cd " "$( readlink -f "$( dirname "$file" )" )" && \[/COLOR]
	**cd** "$( readlink -f "$( dirname "$file" )" )"
	[COLOR="Silver"]echo "msgmerge -U "$localedir"C/LC_MESSAGES/"$textdomain".pot" && \[/COLOR]
	**msgmerge** -U $textdomain".po" $localedir"C/LC_MESSAGES/"$textdomain".pot"
	[COLOR="Silver"]echo $poeditor $textdomain".po" && \[/COLOR]
	**$poeditor** $textdomain".po"

	[COLOR="Silver"]echo "msgfmt -o $textdomain.mo `basename $file`" && \[/COLOR]
	**msgfmt** -o $textdomain.mo `basename $file`
	#**TODO**: for existing .mo - revise only older than .po
done
```

---

### Post by worksofcraft on 2010-08-20
I think there is a whole system in place using autotools but I haven't progressed into learning that yet.

---

