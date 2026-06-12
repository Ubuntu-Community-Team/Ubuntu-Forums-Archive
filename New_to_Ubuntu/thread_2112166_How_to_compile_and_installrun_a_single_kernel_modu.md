---
title: "How to compile and install/run a single kernel module"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by ymsaputra on 2013-02-04
Dear All,

I have a problem to compile and run/install one single kernel module.

For example, I have already installed one packaged kernel (e.g 3.7.1 version) and then I try to change source code from several files in carl9170 modules (drivers/net/wireless/ath/carl9170).

Then, do you know how to compile and then run/install it in the system for that module only (not all modules)?

As far as I know, how to compile is by using :

make modules SUBDIRS=drivers/the_module_directory 
Is it right? and what the other things to do (step by step) after using that command (if it's right)?

After compiling, Do I need to install the system again?



Thank you for the answers

---

### Post by meteorrock on 2013-02-04
> **ymsaputra said:**
> Dear All,

I have a problem to compile and run/install one single kernel module.

For example, I have already installed one packaged kernel (e.g 3.7.1 version) and then I try to change source code from several files in carl9170 modules (drivers/net/wireless/ath/carl9170).

Then, do you know how to compile and then run/install it in the system for that module only (not all modules)?

As far as I know, how to compile is by using :

make modules SUBDIRS=drivers/the_module_directory 
Is it right? and what the other things to do (step by step) after using that command (if it's right)?

After compiling, Do I need to install the system again?



Thank you for the answers

>  carl9170 modules (drivers/net/wireless/ath/carl9170).

Are you trying to compile a module for a wireless driver? There is a tool you can use on ubuntu or other linux builds called "ndiswrapper" that might be able to help you for an easier solution. 

Here is an outside link on how to use this tool. [http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

Hope that helps. :) If you are doing this as an exercise though on learning linux, you should be able to patch your module and you should be set without having to reinstall the system. It will install that single module you are building through the terminal and you should be set. If you are setting up your PATH variables up correctly you should see code compiling in your terminal. When its completed you will be back at the $ prompt in there.



 That is the right command by these links out here. [http://stackoverflow.com/questions/8744087/how-to-recompile-just-a-single-kernel-module](http://stackoverflow.com/questions/8744087/how-to-recompile-just-a-single-kernel-module)

And also here. [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGsQFjAG&url=http%3A%2F%2Fwww.kernel.org%2Fdoc%2FDocumentation%2Fkbuild%2Fmodules.txt&ei=BnUPUcCsCaz8iQKwxIFI&usg=AFQjCNF2AnvjE4Fx3-2vDbeDa-0YIv8rHQ&bvm=bv.41867550,d.cGE](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CGsQFjAG&url=http%3A%2F%2Fwww.kernel.org%2Fdoc%2FDocumentation%2Fkbuild%2Fmodules.txt&ei=BnUPUcCsCaz8iQKwxIFI&usg=AFQjCNF2AnvjE4Fx3-2vDbeDa-0YIv8rHQ&bvm=bv.41867550,d.cGE)

---

### Post by ymsaputra on 2013-02-04
Thank you so much for your answer. It's very helpful.

There is no problem with my wireless driver. Yes, I just want to learn how to compile a single kernel module.

I have already used that command and the last result will display the new .ko for example carl9170.ko. 

Is it right? So that result means that the module is already compiled and installed with new modification and the system will run with new modification of carl9170 module, right?

---

### Post by lle on 2013-02-04
I _think_ you should run 

```
depmod -a
```to activate the new module. Maybe also ```
mkinitramfs -o /boot/initrd.img-<new kernel version> <new kernel version>
```But I'm not 100% sure about the latter, I think it makes the module load at reboot?


I also have a problem related to modules. I compiled the newest 3.8rc5 kernel to get my gigabit cards to work. However, after booting the new kernel the iptables didn't function correctly. 

It's missing all NAT-related modules! Although I had them in my old kernel and I copied the configuration to the new kernel(at least I thought it got copied).

Now I'm struggling to install those missing iptables/netfilter/nat modules to make my router-server to work again.


You said:
> make modules SUBDIRS=drivers/the_module_directory That would compile a single module? In which directory do I run the command? I have my kernel sources in ```
/home/user/git/linux
```

---

### Post by DuckHook on 2013-02-04
> **meteorrock said:**
> Are you trying to compile a module for a wireless driver? There is a tool you can use on ubuntu or other linux builds called "ndiswrapper" that might be able to help you for an easier solution.

Sometimes this is necessary, but it is usually a good idea to avoid ndiswrapper until all other solutions have been exhausted. This is because ndiswrapper is just a translator for windows drivers, which can't be expected to run as functionally or as efficiently as native Linux modules. In most cases, native Linux drivers can be found, but it is admittedly often obscure and convoluted.

---

### Post by bodhi.zazen on 2013-02-04
There are several ways to do this (build a single module):

```
make modules SUBDIRS=drivers/the_module_directory
```

Should work

You then either manually copy the module or run

```
sudo make modules install
```

---

### Post by ymsaputra on 2013-02-04
> **bodhi.zazen said:**
> 

```
sudo make modules install
```

By using this command, it will install all modules or just that single module? I need to install just that single module, is it possible?

Another method is copy the module, How to copy the module and where?

Thank you for your answers

---

### Post by ymsaputra on 2013-02-04
> 
You said:
That would compile a single module? In which directory do I run the command? I have my kernel sources in ```
/home/user/git/linux
```

Inside that directory (linux directory ) you just type that command

---

### Post by williejones on 2013-02-04
> **ymsaputra said:**
> Dear All,

I have a problem to compile and run/install one single kernel module.




Usually when you download the source to compile there will be a _**read me**_ file that will give instructions how to compile and load the module.

---

### Post by meteorrock on 2013-02-05
> **DuckHook said:**
> Sometimes this is necessary, but it is usually a good idea to avoid ndiswrapper until all other solutions have been exhausted. This is because ndiswrapper is just a translator for windows drivers, which can't be expected to run as functionally or as efficiently as native Linux modules. In most cases, native Linux drivers can be found, but it is admittedly often obscure and convoluted.


Thanks. :) That does make sense. Good call on that, I would not of thought of that. :)

---

