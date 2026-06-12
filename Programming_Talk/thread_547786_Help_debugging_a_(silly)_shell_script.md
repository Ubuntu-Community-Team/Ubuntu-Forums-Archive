---
title: "Help debugging a (silly) shell script"
date: 2007-09-10
forum: Programming Talk
---

### Post by aashay on 2007-09-10
```

flag="0"
NAUTILUS_SELECTED_URIS='file:///home/aashay/tempex'
if [ "$*" != '' ]
	then
	NAUTILUS_SELECTED_URIS=$1/$2
	flag=1
fi
#echo $NAUTILUS_SELECTED_URIS
#echo Flag is: $flag
for str in $NAUTILUS_SELECTED_URIS
	do
	substring=${str:7:255}
	status=$(file -b $substring)
	if [ "$status" = "directory" ] 
		then
		echo dir $substring >> /home/aashay/debug
		for subfile in $(ls $substring)
			do
			~/.gnome2/nautilus-scripts/send-to-phone2 $str $subfile
		done
	else
		echo File: $substring
		path="'E:/Unsorted"${1:7:255}"'"
[B]		echo sudo obexftp -u 1 -C $path -p $substring >> temp.sh
		sudo obexftp -u 1 -C $path -p $substring[/B]
		echo file $substring >> /home/aashay/debug
	fi
done
```
As you may see, i'm trying to write a simple nautilus script to upload folders recursively to my cellphone. However, the problem is in the boldface statements... echoing the command to a separate sh and then executing it / pasting everything into the terminal works perfect.
```
aashay@kriz:~/.gnome2/nautilus-scripts$ bash temp.sh
Connecting...done
Sending "E:"... Sending "Unsorted"... Sending "home"... Sending "aashay"... Sending "tempex"... done
Sending "/home/aashay/tempex/chrome-theme.so"...|done
```

 But executing the exact same command through the script itself doesn't 
```
aashay@kriz:~/.gnome2/nautilus-scripts$ ./send-to-phone2
File: /home/aashay/tempex/chrome-theme.so
Connecting...done
Sending "'E:"... failed: 'E:/Unsorted/home/aashay/tempex'
Sending "/home/aashay/tempex/chrome-theme.so"...\failed: /home/aashay/tempex/chrome-theme.so
```

---

