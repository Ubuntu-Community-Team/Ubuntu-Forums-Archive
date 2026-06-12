---
title: "Simple BASH script problem - escaping spaces"
date: 2007-06-19
forum: Programming Talk
---

### Post by matt_b on 2007-06-19
Hi all,

I'm trying to write  a BASH script that I can run at system startup (through rc.local) to start all of my VMware virtual machines in a specific order (amongst other things). VMware make a command available "vmrun" which takes in a start|stop|suspend parameter and a path to a .vmx file (basically a text file), for example: /usr/bin/vmrun start /home/matt/virtualmachines/test/Ubuntu.vmx

The trouble is, some of the paths to the .vmx files contain spaces, and I am having difficulties escaping them and passing them to the vmrun command. Here's what I've got so far:

```
vms[0]="/home/matt/virtualmachines/smoothwall-195/Other Linux 2.4.x kernel.vmx"
vms[1]="/home/matt/virtualmachines/smoothwall-196/Other Linux 2.4.x kernel.vmx"
vms[2]="/home/matt/virtualmachines/server/Windows Server 2003 Enterprise Edition.vmx"
vms[3]="/home/matt/virtualmachines/proxy/Ubuntu.vmx"

for (( vm = 0 ; vm < ${#vms[@]} ; vm++ ))
do

        # Start the virtual machine
        tmp=$(echo ${vms[$vm]} | sed 's/ /\\ /g')
        /usr/bin/vmrun start $tmp

done
```

If I run this script, vmrun complains that it can't find **/home/matt/virtualmachines/smoothwall-195/Other\**

If I run the script in debug mode I can see that $tmp is being set correctly **tmp='/home/matt/virtualmachines/smoothwall-195/Other\ Linux\ 2.4.x\ kernel.vmx'** but when it is being expanded in the vmrun command there are some rogue single quotes **/usr/bin/vmrun start '/home/matt/virtualmachines/smoothwall-195/Other\' 'Linux\' '2.4.x\' kernel.vmx**

I've also tried passing the output of sed directly into vmrun but that doesn't work either as vmrun complains that I've not passed it enough parameters :S **echo ${vms[$vm]} | sed 's/ /\\ /g' | /usr/bin/vmrun start**

I'm new to shell scripting - hope someone can point me in the right direction!

Thanks
matt_b

---

### Post by Bluecircle on 2007-06-19
Can you rename "Other Linux 2.4.x kernel.vmx" to "Other Linux2.4.xkernel.vmx" and then remove the spaces and quotes from the shell script? Will it work then?

---

### Post by matt_b on 2007-06-19
I can rename the .vmx files and replace the spaces with dashes, and this semi-works: the script works correctly but vmware doesn't as renaming the .vmx files causes problems in vmware.

---

### Post by jyba on 2007-06-19
Instead of...
```
tmp=$(echo ${vms[$vm]} | sed 's/ /\\ /g')
```
...try
```
tmp=$(echo "'${vms[$vm]}'")
```
It should pass each of your paths to vmrun with single quotes around them.

---

### Post by bigboy_pdb on 2007-06-19
I checked your script and it looks as though it should work.

Perhaps instead of using:
        # Start the virtual machine
        tmp=$(echo ${vms[$vm]} | sed 's/ /\\ /g')
        /usr/bin/vmrun start $tmp

You could try:
        /usr/bin/vmrun start "'"${vms[$vm]}"'"

---

### Post by HackingYodel on 2007-06-19
Hi matt_b,

I have two options I think will work for you.

Bash will do variable substitution for us without **sed**:
```
vms[0]="/home/matt/virtualmachines/smoothwall-195/Other Linux 2.4.x kernel.vmx"
vms[1]="/home/matt/virtualmachines/smoothwall-196/Other Linux 2.4.x kernel.vmx"
vms[2]="/home/matt/virtualmachines/server/Windows Server 2003 Enterprise Edition.vmx"
vms[3]="/home/matt/virtualmachines/proxy/Ubuntu.vmx"

for (( vm=0; vm < ${#vms[@]}; vm++ ))
do

	/usr/bin/vmrun start "${vms[$vm]// /\\ }"   # ${var[num]//pattern/replace} we use \\ to escape the \

done
```

or perhaps try this, you may not need to escape the spaces at all.

```
vms[0]="/home/matt/virtualmachines/smoothwall-195/Other Linux 2.4.x kernel.vmx"
vms[1]="/home/matt/virtualmachines/smoothwall-196/Other Linux 2.4.x kernel.vmx"
vms[2]="/home/matt/virtualmachines/server/Windows Server 2003 Enterprise Edition.vmx"
vms[3]="/home/matt/virtualmachines/proxy/Ubuntu.vmx"

for (( vm=0; vm < ${#vms[@]}; vm++ ))
do

	/usr/bin/vmrun start "${vms[$vm]}"

done
```

---

### Post by matt_b on 2007-06-19
Thanks for the replies - this one seemed to do the trick:

```
vms[0]="/home/matt/virtualmachines/smoothwall-195/Other Linux 2.4.x kernel.vmx"
vms[1]="/home/matt/virtualmachines/smoothwall-196/Other Linux 2.4.x kernel.vmx"
vms[2]="/home/matt/virtualmachines/server/Windows Server 2003 Enterprise Edition.vmx"
vms[3]="/home/matt/virtualmachines/proxy/Ubuntu.vmx"

for (( vm=0; vm < ${#vms[@]}; vm++ ))
do

	/usr/bin/vmrun start "${vms[$vm]}"

done
```

Using "'" produced odd results in the debug window **/usr/bin/vmrun start ''\''/home/matt/virtualmachines/server/Windows Server 2003 Enterprise Edition.vmx'\'''**

I'm still not sure why I couldn't pipe the output into vmrun..?

Thanks again all,
matt_b

---

### Post by Mr. C. on 2007-06-19
> **bigboy_pdb said:**
> You could try:
        /usr/bin/vmrun start "'"${vms[$vm]}"'"
This wouldn't work, because it is the result of the variable substitution that you want quoted; your example would pass a string like:
```

  'some
   thing
   wrong'
```

to the vimrun program.

[quote=matt_b]I'm still not sure why I couldn't pipe the output into vmrun..?[/quote]
Because arguments and STDIN are two different things.  In otherwords, the following two are not equivalient:

```
   ls -a
   echo -a | ls
```
and in fact, the latter one does not work as expected.

MrC

---

### Post by matt_b on 2007-06-20
Ahh I see, thanks for the pointer.

matt_b

---

### Post by bigboy_pdb on 2007-06-20
I'm so sorry about that post.

After I saw HackingYodel's solution I realized what I had posted was wrong. I've been using awk quite a bit lately and the thing that I posted must have been some strange combination of awk and bash from my mind.

---

