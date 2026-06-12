---
title: "System Information script"
date: 2007-08-18
forum: Programming Talk
---

### Post by jayk121121 on 2007-08-18
Hello.  I wrote a very simple shell script to print system information.  This is it:
```
#!/bin/bash
#Copyright 2007 Jay Karandikar
#
#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 3 of the License, or
#(at your option) any later version.
#
#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
#Change the next line to personalize this script.
echo "This is for the Dell desktop."
echo ""
echo ""
#System Information
function sysinfo {
	echo "System Information:"
	echo ""
	echo ""
	lspci -v
	cat /proc/cpuinfo
	cat /proc/meminfo
	echo ""
	echo ""
}
#Filesystems
function filesys {
	echo "Filesystems:"
	echo ""
	echo ""
	cat /etc/fstab
	mount
}
#If statement to see if there are any arguments.
if [ "$1" = "-s" ]; then
	sysinfo
else if [ "$1" = "-f" ]; then
	filesys
else
	sysinfo
	filesys
fi
```
For some reason, it returns this:
```
This is for the Dell desktop.


./sysinfo: line 49: syntax error: unexpected end of file
```
If I comment out the:
```
else if [ "$1" = "-f" ]; then
	filesys
```
then it works properly, but then I would not be able to make it display only filesystem information.

Can anyone please tell me what is wrong?  Also, if you have any suggestions about other commands that I can put in script, that would be good too.

---

### Post by dustigroove on 2007-08-18
I'm a neophyte when it comes to scripting... but should that "else if" be "elif"?

---

### Post by jayk121121 on 2007-08-18
Thank you very much.  That solved the problem.  Please give more system information commands if you have any.

---

