---
title: "Help with wireless script"
date: 2006-02-15
forum: Programming Talk
---

### Post by zachtib on 2006-02-15
Im writing a script to gui-fy connection to out wireless network at school.

The GUI is basically just a frontend for wpa_supplicant, written in bash

exerpt:
```
CONNECTED="false"
	WPA_STATUS=""
	WPA_LOG=$HOME/wpa.log
	(
	echo "10"
	gnome-terminal --command="sudo wpa_supplicant -w -i${WIFI_DEV} -D${WIFI_DRV} -c${CONF_FILE} -dd"
	while [ ${CONNECTED}=="false" ]; do
		sudo wpa_cli status &> $WPA_LOG
		#echo "# Reading" ; sleep 1
		exec < $WPA_LOG
		while read line
		do
			WPA_STATUS="$line"
		done
		#WPA_STATUS=`sudo wpa_cli status`
		gnome-terminal --command="sudo wpa_supplicant -w -i${WIFI_DEV} -D${WIFI_DRV} -c${CONF_FILE} -dd"
		echo "# $WPA_STATUS" ; sleep 10
	done
	)|
        zenity --progress --title="UofLConnect" \
          --text="Connecting" --percentage=0 \
	  --width=500 --pulsate

	if [ "$?" = -1 ] ;
	then
        	zenity --error --text="Connection cancelled."
		sudo killall wpa_supplicant
		exit 1
        fi
```

the problem is, it never authenticates while the gui is up.  If I cancel the window once it has started, it will finish authenticating.  I think the wpa_cli calls are interupting wpa_supplicant.  Does anyone know a better way to communicate with wpa_supplicant.  Also, is there a way to make this line:
```
gnome-terminal --command="sudo wpa_supplicant -w -i${WIFI_DEV} -D${WIFI_DRV} -c${CONF_FILE} -dd"
```
pop up a gksudo dialog and then background instead of my current solution, which pops up a gnome-terminal.
Connecting to the wireless at my school is a pain, and I'm trying to make it easier on people.  If anyone has any suggestions, I's appreciate them. If anyone wants, I'll post the full source code

---

### Post by jpkotta on 2006-02-15
Try ```
gnome-sudo *command*
```
That will get you a sudo dialog like from the menus.

---

### Post by zachtib on 2006-02-15
thanks, I'll try that

---

