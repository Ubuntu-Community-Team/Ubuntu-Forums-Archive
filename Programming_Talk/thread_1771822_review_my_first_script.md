---
title: "review my first script"
date: 2011-05-30
forum: Programming Talk
---

### Post by mechanizedmedic on 2011-05-30
this is my first bash script. i created it by doing lots of googling and was hoping someone could review it for me to make sure i'm on the right track.
 
[COLOR=red]Updated to reflect suggestions! Thank you all![/COLOR]
 
```
#!/bin/bash
#designed for Ubuntu 10.10 variants
script_name="brothermfc7340.sh"
 
# Script must run as root
if [ $(id -u) -ne 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi
 
# make the required directories
mkdir /usr/share/cups/model /var/spool/lpd
 
#install scan dependancies
apt-get install -y sane-utils psutils
 
#apparmour in complain model
aa-complain cupsd
 
#download and install .deb files
 
if [ $(uname -m) == 'x86_64' ]; then
# 64-bit
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.amd64.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.amd64.deb brscan-skey-0.2.1-3.amd64.deb brmfcfaxcups-1.0.0-1.i386.deb
else
# 32-bit
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.i386.deb brscan-skey-0.2.1-3.i386.deb brmfcfaxcups-1.0.0-1.i386.deb
fi
 
#stop cups
/etc/init.d/cups stop
 
#edit cups printers.conf file to add printing and faxing
sed -i '/CUPSD IS RUNNING/a\
<Printer BRFAX>\n
Info BRFAX\n
MakeModel Brother BRMFCFAX for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306719206\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brfaxfilter\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n
<Printer Brother_MFC-7340>\n
Info Brother MFC-7340\n
MakeModel Brother MFC7340 for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306715389\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brlpdwrapperMFC7340\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n' /etc/cups/printers.conf
 
#start cups
/etc/init.d/cups start
 
#enable normal user to access the scanner
sed -i '/autosuspend/i\# Brother scanners\nATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"' /lib/udev/rules.d/40-libsane.rules

```

---

### Post by epicoder on 2011-05-30
<grammarnazi>
> **mechanizedmedic said:**
> **T**his is my first bash script. **I** created it by doing lots of googling and was hoping someone could review it for me to make sure **I**'m on the right track.
The shift key is there for a reason. ;)
</grammarnazi>

Your script looks fine to me, except for one possible catch: I think uname -m may output "amd64" instead of "x86_64" in some cases. Don't quote me on it though. Also, you might consider using ```
if [ `id -u` = 0 ]
```instead of $USER as someone can redefine $USER to make your script think that it's being run as root when it's not. That's just my personal preference though.

---

### Post by wojox on 2011-05-30
x86_64 needs the **ia32-libs** installed to run. Looks good.

---

### Post by hakermania on 2011-05-31
> **sh228 said:**
> <grammarnazi>

The shift key is there for a reason. ;)
</grammarnazi>

Your script looks fine to me, except for one possible catch: I think uname -m may output "amd64" instead of "x86_64" in some cases. Don't quote me on it though. Also, you might consider using ```
if [ `id -u` = 0 ]
```instead of $USER as someone can redefine $USER to make your script think that it's being run as root when it's not. That's just my personal preference though.

when comparing integers, instead of '=' it is better to use -eq (equal).
Also, try to avoid the ` `, use better $(id -u)

---

### Post by mechanizedmedic on 2011-05-31
> **sh228 said:**
> Your script looks fine to me, except for one possible catch: I think uname -m may output "amd64" instead of "x86_64" in some cases. Don't quote me on it though. 

I searched around a little more and couldn't find any "amd64" outputs. Would it hurt anything to use [ $(uname -m) == 'x86_64' -o 'amd64' ] instead of defining machine type? 

> **wojox said:**
> x86_64 needs the **ia32-libs** installed to run. Looks good.
thank you!

> **hakermania said:**
> when comparing integers, instead of '=' it is better to use -eq (equal).
Also, try to avoid the ` `, use better $(id -u)

for future knowledge, what is the issue using '=' with integers?
also, what are the potential problems with using ` `?

---

### Post by dwhitney67 on 2011-05-31
> **mechanizedmedic said:**
> 
for future knowledge, what is the issue using '=' with integers?

Read here: [http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

> **mechanizedmedic said:**
> 
also, what are the potential problems with using ` `?
None that I can think of; I think it is merely personal preference.  Some developers have a hard time seeing those back-quotes (-tick), and they can be confused with the regular single-quote character.

Personally, I use the ` ` because it is usable in both bash and tcsh.  In the context of creating a sub-shell, the $( ) does not work with tcsh.

P.S.  Beware of /bin/sh.  On some systems it references /bin/bash, on others (eg. Ubuntu), it references /bin/dash.  The latter does not fully support all of bash's features.

---

### Post by epicoder on 2011-06-01
> **mechanizedmedic said:**
> 
also, what are the potential problems with using ` `?
Backticks are rather hard to nest compared to $(). Also, $() runs the command in a subshell, while backticks don't. Normally, it's easier to use $() and it is the accepted "standard" in bash scripts. However, as your first line tells the system to execute with /bin/sh, it is not a good idea to use $() because /bin/sh can link to /bin/dash on some systems (including ubuntu), which doesn't support $().

---

### Post by kaibob on 2011-06-01
> **mechanizedmedic said:**
> also, what are the potential problems with using ` `?

sh228 has covered the most important points on this issue, but the following contains a little additional information:

[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

---

### Post by Vox754 on 2011-06-01
> **dwhitney67 said:**
> ...

P.S.  Beware of /bin/sh.  On some systems it references /bin/bash, on others (eg. Ubuntu), **it references /bin/dash.  The latter does not fully support all of bash's features.**

[quote=http://mywiki.wooledge.org/BashFAQ/082]
The only time backticks are preferred is when writing code for the oldest Bourne shells, which are not POSIX compliant. See POSIX standard and section "2.6.3 Command Substitution" for $(). [/quote]
As others have pointed it out, the issue is compatibility with old systems, essentially.

If you are writing for old shells, use #!/bin/sh as the shebang, and only use old-school, standard functions, such as ` `.

If you are definitely using a new shell, please use the correct shebang, such as #!/bin/bash, and use modern constructs, such as $( ).

---

### Post by mechanizedmedic on 2011-06-03
> **Vox754 said:**
> As others have pointed it out, the issue is compatibility with old systems, essentially.
 
If you are writing for old shells, use #!/bin/sh as the shebang, and only use old-school, standard functions, such as ` `.
 
If you are definitely using a new shell, please use the correct shebang, such as #!/bin/bash, and use modern constructs, such as $( ).
 
\\:D/oooohhhhhh! that makes more sense than the personal pref explainations i've seen.
 
thank you!

---

### Post by Vaphell on 2011-06-03
consider using a variable that will inject proper string in that wget/dpkg part, assuming it's essentially the same in both cases
```
if ...; then
  arch='amd64'
else
  arch='i386'
fi
wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.${arch}.deb ...
dpkg -i --force-all brmfc7340lpr-2.0.2-1.${arch}.deb ...
```

---

### Post by mechanizedmedic on 2011-06-05
> **Vaphell said:**
> consider using a variable that will inject proper string in that wget/dpkg part, assuming it's essentially the same in both cases
```
if ...; then
  arch='amd64'
else
  arch='i386'
fi
wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.${arch}.deb ...
dpkg -i --force-all brmfc7340lpr-2.0.2-1.${arch}.deb ...
```

wonderful! thank you!

---

### Post by tgm4883 on 2011-06-05
Instead of using this code for the script_name

```
#!/bin/bash
#designed for Ubuntu 10.10 variants
script_name="brothermfc7340.sh"
 
# Script must run as root
if [ $(id -u) -eq 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi
```

you could use $0 instead. This will print the command used to run the script and will work even if someone changes the name of the script or runs it with the full directory path.

```
echo "Use 'sudo $0' then enter your password when prompted."
```

---

