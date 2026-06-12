---
title: "Switching focus Expect script"
date: 2011-11-23
forum: Programming Talk
---

### Post by conradin on 2011-11-23
Hi all,
I have an expect script that opens up 
VMD. From within tha, I would like to send the VMD console the command to launch tkconsole. Doing this allows me to use both VMD & TCL commands.  I can do this manualy, but I cannot seem to have the window shift control to the VMD terminal via the script. 

the code below, just launches VMD, then a seperate instance of tkconsole, in which I do not have access to VMD commands. 

```
#!/usr/bin/expect
spawn vmd
expect "vmd >"
send "tkcon\r"
expect "%"
echo "hello cruel world! \n\n my life is over\n\r"
expect "%"

```


I need the focus to be shifted to the vmd session, then the tkcon session, so I can proceed with sending more commands to the vmd initiated tkcon session. 
Does anyone have any ideas?

---

