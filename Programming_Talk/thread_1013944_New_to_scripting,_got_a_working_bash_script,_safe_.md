---
title: "New to scripting, got a working bash script, safe to deploy in Windows environ?"
date: 2008-12-17
forum: Programming Talk
---

### Post by john_spiral on 2008-12-17
Hi,

I've got a working one liner script that gives me a directory listing on a remote Windows machine. I know it's not such :p. 

I'm going to be running it against a few thousand machines from an Ubuntu box running 8.1. *Will it be safe*?

sample:

ping machine1 | grep 'Reply'; if [ $? == 0 ]; then find //machine1/c$/DOCUME~1 -maxdepth 1 -type d >> output.txt; fi;
ping machine2 | grep 'Reply'; if [ $? == 0 ]; then find //machine2/c$/DOCUME~1 -maxdepth 1 -type d >> output.txt; fi;

Once I've run this audit I intend copying *.lnk files from all the machines to the Ubuntu box. What tools should I look at for connecting to the Windows environment with specific credentials? 

thanks in advance.

John

---

### Post by lykwydchykyn on 2008-12-17
Does this actually work for you?  I didn't think "find" would actually connect directly to a smb share like that.  It doesn't work here for me.

I would think you'd want to use smbmount to mount the C$ share to a temp folder and then run your "find" command against the temp folder.

Also, does the "ping machine1|grep "Reply"" actually work?  I don't see the text "reply" in any responses from ping (either good or bad).  Also, without the -c switch ping on Linux will run forever.

---

### Post by Pvt_Ryan on 2008-12-17
Reply shouldn't work.

```

if [ `ping $machine -c1 | grep -c -i "64 bytes from ${machine}"` -eq 0 ]; then
mount ...
find ...
umount ...
fi

```

Heres a script I have for pinging cluster nodes:
[http://projects.ninet.org/index.php/Node_Availability](http://projects.ninet.org/index.php/Node_Availability)

---

### Post by john_spiral on 2008-12-17
> **lykwydchykyn said:**
> Does this actually work for you?  I didn't think "find" would actually connect directly to a smb share like that.  It doesn't work here for me.

I would think you'd want to use smbmount to mount the C$ share to a temp folder and then run your "find" command against the temp folder.

Also, does the "ping machine1|grep "Reply"" actually work?  I don't see the text "reply" in any responses from ping (either good or bad).  Also, without the -c switch ping on Linux will run forever.

Hi, forgot to mention that I developed the above script in a [[COLOR="Blue"]_cygwin_[/COLOR]]("http://www.cygwin.com/") bash under Windows XP. 

Guess I need to make some changes to make the script work under Ubuntu.

I intend running the script against 3000 machines, is a smbmount my only option.

Thanks

John

---

### Post by john_spiral on 2008-12-17
> **Pvt_Ryan said:**
> Reply shouldn't work.

```

if [ `ping $machine -c1 | grep -c -i "64 bytes from ${machine}"` -eq 0 ]; then
mount ...
find ...
umount ...
fi

```

Heres a script I have for pinging cluster nodes:
[http://projects.ninet.org/index.php/Node_Availability](http://projects.ninet.org/index.php/Node_Availability)

see my above post, I would need to change the grep command with an Ubuntu ping reply.

---

### Post by Pvt_Ryan on 2008-12-17
My version is linux specific.

---

### Post by john_spiral on 2008-12-17
thanks for the code Pvt_Ryan,

Would the "64 bytes" always be true in your grep statement?

**_More info on my script_**

I was looking for a one liner command that I could plug into a spreadsheet column of computer names.

---

### Post by Pvt_Ryan on 2008-12-17
yes it is always true.

for a spreadsheet use a csv file. 

then you could do something like:

machineName, MachineIP
dozer,192.168.2.1
dozer2,192.168.2.2
dozer3,192.168.2.3

```

i=0;
for $line in `cat spreadsheet.csv`;
do
ip=`echo $line | cut -f2 -d","`;
if [ $i -ne 0 ]; then
  if [ `ping $ip -c1 | grep -c -i "64 bytes from ${ip}"` -eq 0 ]; then
    ....
  else
    echo "$ip could not be pinged" >> /var/log/mylogfile;
  fi
fi
i=1;

```
i is used as the 1st line of the csv is headers.

---

### Post by Pvt_Ryan on 2008-12-17
just updated the script as i forgot to pull the ip from the file.

---

### Post by lykwydchykyn on 2008-12-17
The whole ping thing may not be necessary, if you smbmount.  If smbmount fails, you can just skip the find command. e.g.:

```

smbmount //machine1/C$ ~/temp -o user=someuser,pass=somepass
if [ $? -ne 0 ]; then
find #etc etc
fi

```

You could also use smbclient to attach to the machines, but you wouldn't be able to use "find"; that approach would only work if you know the specific directory you want to list.  To use "find", you'll need to mount the remote system locally, AFAIK.

---

### Post by mssever on 2008-12-17
Why parse ping's output? Just use its exit code. ```
if ping -c1 -w2 somehost >/dev/null 2>&1; then
  # do stuff
fi
```

---

### Post by john_spiral on 2009-01-06
thanks for all the input so far.

I finally settled on the below one liner:

```
smbmount //WINDOWSMACHINE/C$ /mnt/win sec=ntlmv2i -o user=USERNAME,pass=PASSWORD,ro; if [ $? == 0 ]; then cd /mnt/win/DOCUME~1; find . -maxdepth 1 -type d | sed "s#^.#$(pwd)#" >> /home/myusername/Desktop/dir_list.txt; cd /mnt; fi; smbumount /mnt/win/; sleep	1 
```

Gives a directory listing for 'Documents and Settings' on machine 'WINDOWSMACHINE'.

Ideally it would be nice to extend the script to read a list of machines from a text file and then preform an action on the output of: ```
find . -maxdepth 1 -type d | sed "s#^.#$(pwd)#"
```

I had a go at Pvt_Ryan's csv script but I'm punching above my weight.

I've finally settled on compositing a script using Open Office Calc, pasting the final contents into a text file. Beautiful no, but it works.    

Thanks again

John

---

