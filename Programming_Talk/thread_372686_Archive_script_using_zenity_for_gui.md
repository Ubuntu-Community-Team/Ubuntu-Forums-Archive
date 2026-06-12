---
title: "Archive script using zenity for gui"
date: 2007-02-28
forum: Programming Talk
---

### Post by highneko on 2007-02-28
A script to make zipping, unzipping, testing zips, unraring, and tar archiving easier. Just run it from the terminal because it uses the current directory a lot.

Made a little script for myself and thought sharing it with everyone would be a good idea. Just discovered a program called zenity which creates gui for scripts. The old version without zenity can be found here: [http://pastebin.ca/375939](http://pastebin.ca/375939)
```
#!/bin/bash

# Archive files easier by highneko

if [ ! -e "/usr/bin/zenity" ]; then
	sudo apt-get install zenity
fi

choice="$(zenity --width=400 --height=450 --list --column "Archive Options" \
"Backup all files in current directory using tar gzip" \
"Test all zip archives in current directory" \
"Unrar all archives in current directory" \
"Unzip all archives in current directory" \
"Unzip archives directly into the current directory" \
"Unzip using tests to check if directory exists" \
"Zip all files and folders in current directory" \
"Zip each folder in current directory into an archive")"

warning() {
	if ! zenity --question --title "Alert" --text "${choice}
	Current directory: ${PWD}
	Do you want to continue?"; then
		exit 0
	fi
}

case "${choice}" in
	"Backup all files in current directory using tar gzip" )
		warning
		tar -czf "${PWD##*/}.tgz" *
	;;
	"Test all zip archives in current directory" )
		warning
		for x in *.zip; do zip -T "$x"; done
	;;
	"Unrar all archives in current directory" )
		warning
		for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
	;;
	"Unzip all archives in current directory" )
		warning
		for x in *.zip; do mkdir "${x%.zip}" && cd "${x%.zip}" && unzip "../$x" && cd ..; done
	;;
	"Unzip archives directly into the current directory" )
		warning
		for x in *.zip; do unzip "$x"; done
	;;
	"Unzip using tests to check if directory exists" )
		warning
		for i in *.zip; do if zipinfo "$i" | grep -q '/'; then unzip "$i"; else mkdir "${i%.zip}" && cd "${i%.zip}" && unzip "../$i" && cd ..; fi; done
	;;
	"Zip all files and folders in current directory" )
		warning
		zip -r ${PWD##*/}.zip *
	;;
	"Zip each folder in current directory into an archive" )
		warning
		for x in *; do if [ -d "$x" ]; then cd "$x" && zip -r "../${x}.zip" * && cd ..; fi; done
	;;
esac

exit 0
```

---

