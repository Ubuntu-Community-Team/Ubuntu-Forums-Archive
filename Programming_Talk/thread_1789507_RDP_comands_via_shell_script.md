---
title: "RDP comands via shell script"
date: 2011-06-23
forum: Programming Talk
---

### Post by conradin on 2011-06-23
Hi all, ( I have a feeling some one will try to rip me a new 1 over this but here it goes.)
The place where I am working has 20 windows computers with remote desktops used for admins to make various system modifications. Thats fine, but for the more repeitive admin tasks, I would like to write an automation script to do the logins and then execute generate and execute batch scripts in the windows sessions. 

so, I can create an expect script to get me as far as the login to the RDP session for the remote computers. But the down side is when the windows session launches, I have no more terminal output to "Expect" So using Expect becomes useless. Then there is the issue of how to send commands to the windows remote environment when I'm not getting any feed back from the terminal. I am thinking SURELY, there must be terminal interactions going on, is there a way I can access that info?

Here is the RDP login code I have thus far, when I got stuck not knowing what to "expect" next.
Any idea? I would much like to automate windows Management with Linux, that makes a whole lot os sense to me.
```

#!/usr/bin/expect -f
 
#open RDP sessions. 

set timeout 4
set dictionary [lindex $argv 0]
set file [lindex $argv 1]
set user [lindex $argv 2]

if {{llength $argv] != 3} {
puts stderr "Usage: $argv0 <Dictionary-file> <hosts-file> <users>\n"
exit }

set tryHost [open $file r]
set tryPass [open $dictionary r]
set passwords [read $trypass]
set hosts [read $tryHost]

foreach ip $hosts {
	foreach passwd $passwords {
		spawn rdesktop -u $user -p $passwd $ip
		

```

---

### Post by slavik on 2011-06-23
powershell
sshd via cygwin

---

### Post by conradin on 2011-06-25
I was hoping for a way to do it with out additional windows software installations required. 
How ever, 
I do like the powershell idea, 
I can access that via the command```
rdesktop -u <user> -p <pass> -s <powershell> 192.168.111.111
``` I think that will work.

---

