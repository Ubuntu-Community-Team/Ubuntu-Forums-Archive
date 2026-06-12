---
title: "HOWTO: Application specific mouse/keyboard settings (window matching)"
date: 2007-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by tweedledee on 2007-03-10
Here is a simple script you can use to provide application specific mouse and/or keyboard settings (when used in conjunction with xbindkeys).

Prequesites: working mouse and/or keyboard, working xbindkeys, and xte (from xautomation package).  See here for help getting your mouse initially running and working with these programs: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441) (or numerous other posts).

Here is the script:```
#!/bin/bash

# Run one of the following terminal commands and click on window to get item value
# 	To get Class, run:
#		xprop |nawk -F = '/WM_CLASS/ {N=split($2, A, ", ");  gsub(/\"/,"",A[2]); print A[2]; exit;}'
# 	To get AltClass, run:
#		xprop |nawk -F = '/WM_CLASS/ {N=split($2, A, " ");  gsub(/\"/,"",A[1]);  gsub(/,/,"",A[1]); print A[1]; exit;}'
#
# If the window cannot be clicked on (e.g., fullscreen apps), then run these instead, switching to the app within 5 seconds
#	of issuing the command, and then back to the terminal a few seconds later
#	To get Class, run:
#		sleep 5; xprop -id `xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'` |nawk -F = '/WM_CLASS/ {N=split($2, A, ", ");  gsub(/\"/,"",A[2]); print A[2]; exit;}'
#	To get AltClass, run:
#		sleep 5; xprop -id `xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'` |nawk -F = '/WM_CLASS/ {N=split($2, A, " ");  gsub(/\"/,"",A[1]);  gsub(/,/,"",A[1]); print A[1]; exit;}'
#
# You should generally only need Class; AltClass is only useful if Class is ambigious (usually AltClass is more ambigious)

Class=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_CLASS/ {N=split($2, A, ", ");  gsub(/\"/,"",A[2]); print A[2]; exit;}'`
#AltClass=`xprop -id \`xprop -root |nawk '/_NET_ACTIVE_WINDOW/ {print $5; exit;}'\` |nawk -F = '/WM_CLASS/ {N=split($2, A, " ");  gsub(/\"/,"",A[1]);  gsub(/,/,"",A[1]); print A[1]; exit;}'`

case "$Class" in
	OpenOffice.org\ 2.0)
		/usr/bin/xte 'keydown Control_L' 'keydown Shift_L' 'key u' 'keyup Shift_L' 'keyup Control_L' &
		;;
	Gnumeric)
		/usr/bin/xte 'keydown Control_L' 'keydown Shift_L' 'key u' 'keyup Shift_L' 'keyup Control_L' &
		;;
	"")		# this matches a window that does not have a Class name, e.g., VLC or xine in fullscreen mode
		;;
	*)		# this is the default action
		/usr/bin/xte 'mouseclick 2' &
		;;
esac
exit 0
```
And the lines in xbindkeysrc to trigger it:```
"/usr/local/bin/middle-button.bash &"
b:9 + Release
```
This particular example uses a small button on my trackball as a multi-purpose tool - usually it maps to the middle-click function, but in some programs (Gnumeric & OpenOffice), it instead provides CTRL+SHIFT+U to trigger entry for a unicode character (I insert a lot of special characters).

To use this, simply copy the script code to a file on your system and make that file executable.  Then invoke that file with xbindkeys as you woudl normally issue a command.  In the script, follow the comments lines on how to get the unique indentifier for each program (paste one of the terminal codes to the terminal, press ENTER, and click on the window of interest); then use those identifiers in the case statement (just replace the examples that are present).

If the "Class" commands don't give you a unique identifier, try the "AltClass" approach, just changing the "$Class" in the case statement to "$AltClass" if you use that instead.  You can use both by using 2 case statements.  You can also match on the window title (the displayed text in the title bar), but that approach requires more effort; see this thread for how to do that: [http://www.ubuntuforums.org/showthread.php?t=319519](http://www.ubuntuforums.org/showthread.php?t=319519).

The four examples currently present illustrate the main points: that white space (spaces) in the program's indentifier must be escaped (i.e., have a \ in front of them); everything is case sensitive; "" will match a program without a special name (very few - but note that it will match all of them!); and * will match anything "in general."

Also note that if you wish to do as I have done here and simply pass a command through to most programs, you must not have that button mapped to "itself."  Specifically above, I do not have button 9 mapped to button 2 (the middle button) using xmodmap or other means - nothing on my mouse is mapped to position 2.  This is because if you trap Button 2 and send it to the script, and it then tries to execute a Button 2 event, you end up in an endless loop.  This is only a problem if you are using a mouse button to possibly send a mouse event or use a keyboard key to send a keyboard event, and is easy to work around with a mouse (simply map the multi-function button to a non-special position).

Please post with any problems, and I will try to help resolve them.

---

