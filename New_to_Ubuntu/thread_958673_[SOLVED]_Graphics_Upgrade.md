---
title: "[SOLVED] Graphics Upgrade"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Evil79 on 2008-10-25
Greetings,

Kindly iam a new member to Ubuntu, and trying to update everything that i can from the "Synaptic Package Manager" so i can get better graphics.

However i came to know that the SPM is only to add programs or updates to programs. and not for adding graphic updates for my Graphic card.

Thus kindly i need your help to upgrade my graphics card in order to get the better graphic effects from Ubuntu.

for your information Iam using an HP Laptop, nVidia Graphics card.

If you need any other details please fell free to ask. because i can't find anything in the "Hardware Drivers" & "Update Manager" options.

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by tompickles on 2008-10-25
Don't quite understand what you mean by Better Graphics. Do you mean so you can use desktop effects? If you, as you are nVidia, you probabily need to use the proprietry nVidia driver, which should be there in Restricted Driver Manager

---

### Post by Evil79 on 2008-10-25
> **tompickles said:**
> Don't quite understand what you mean by Better Graphics. Do you mean so you can use desktop effects? If you, as you are nVidia, you probabily need to use the proprietry nVidia driver, which should be there in Restricted Driver Manager
Yes Indeed that is what i mean, However i can not find "Restricted Driver Manager", i think i looked every where. and added all the sub links under all of the options.

However that doesn't mean that iam 100% sure because iam still new to Ubuntu thus that makes the percentage of me being worng almost 100%.

Would appreciate the help please.

Kind regards,
Evil

---

### Post by Evil79 on 2008-10-26
Again i tried looking under any option that could lead to Upgrades but with no luck.

What iam trying to do here is find a way to Upgrade my VGA card inorder to activate the disktop graphic options. so i can have better graphic options.

Many thanks and appreciation in advance.

Kind regards,
Evil

---

### Post by fornix on 2008-10-26
Maybe this is what you are asking for...
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by ardvark71 on 2008-10-26
> **Evil79 said:**
> Again i tried looking under any option that could lead to Upgrades but with no luck.

What iam trying to do here is find a way to Upgrade my VGA card inorder to activate the disktop graphic options. so i can have better graphic options.

Many thanks and appreciation in advance.

Hi...

Why do you call yourself that, is that what you feel? :frown:

Can you post the results from this command...

```
lspci
```

It's important to know which chipset you have as the driver packages listed in the link above will depend on it. :)

Best Regards...

---

### Post by Evil79 on 2008-10-26
> **fornix said:**
> Maybe this is what you are asking for...
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

Great simply great that is what i was looking for. i will download those drivers when i get back from work, hopfuly desktop graphics will work by then.

Many thanks "fornix"

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-26
> **ardvark71 said:**
> Hi...

Why do you call yourself that, is that what you feel? :frown:

Can you post the results from this command...

```
lspci
```

It's important to know which chipset you have as the driver packages listed in the link above will depend on it. :)

Best Regards...

Unfortunately iam not 100% sure which chipset do i have for my nVidia vga card. simply because it used to be a Laptop with Vista on it. so i click a button and the updates are done. but with Ubuntu its not that easy.

regardless, once i get back from work i will post the screen shot of the outcome of that code you wrote. so you can understand it better.

Many thanks "ardvark71"

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-26
Ok i red and tried those but unfortunately when i tried typing

so this is a screen shot from the terminal when i try typing either of the following:

nvidia-xconfig
OR
sudo nvidia-xconfig

Now just so i can be honest. i do not know or understand what those comands do. i just know that sudo means do or execute i think. and that the code mentions nvidia which is my VGA brand. 

[[img]http://xs432.xs.to/xs432/08430/snapshot1246.png[/img]](http://xs.to)

Many thanks and appreciation in advance.

Kind regards,
Evil

---

### Post by Evil79 on 2008-10-26
> **Evil79 said:**
> Unfortunately iam not 100% sure which chipset do i have for my nVidia vga card. simply because it used to be a Laptop with Vista on it. so i click a button and the updates are done. but with Ubuntu its not that easy.

regardless, once i get back from work i will post the screen shot of the outcome of that code you wrote. so you can understand it better.

Many thanks "ardvark71"

Kind regards,
Evil.

[[img]http://xs232.xs.to/xs232/08430/snapshot2108.png[/img]](http://xs.to)

And this is the screen shot from the terminal after typing what you asked "ardvark71".

Hope this helps, also not all of the data is showing.

Kind regards,
Evil

---

### Post by ardvark71 on 2008-10-26
Hi...

You have a Nvidia GeForce 8600M GS, the same as I have and it appears supported in Ubuntu 8.04 natively. ;)

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)

Did you follow the instructions in the "how-to" page provided, under "Instructions"...

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

"Ubuntu 8.04 Hardy Heron
Go to System->Administration->Hardware Drivers and check the box to enable the restricted drivers for your NVIDIA card if the option is provided. 

The Hardware Drivers tool may not work properly on machines that have previously used third party tools like 'Envy' or manual installation to install previous drivers. You should remove those drivers before attempting to install using the built in tool. 

If your card does not appear in this list of cards known by Ubuntu 8.04 NVIDIA binary drivers (e.g. the 9600 GT) then there is no Ubuntu 8.04 provided binary driver. For unsupported workarounds try the links in See Also. 


Ubuntu 7.10 Gutsy Gibbon and Ubuntu 7.04 Feisty Fawn
For Ubuntu 7.10 and Ubuntu 7.04 the recommended way to install the binary drivers is to use System->Administration->Restricted Drivers Manager. This will try and automatically choose the correct driver version."

Did this resolve it? :)

Best Regards...

---

### Post by Evil79 on 2008-10-27
> **ardvark71 said:**
> Hi...

You have a Nvidia GeForce 8600M GS, the same as I have and it appears supported in Ubuntu 8.04 natively. ;)

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)

Did you follow the instructions in the "how-to" page provided, under "Instructions"...

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

"Ubuntu 8.04 Hardy Heron
Go to System->Administration->Hardware Drivers and check the box to enable the restricted drivers for your NVIDIA card if the option is provided. 

The Hardware Drivers tool may not work properly on machines that have previously used third party tools like 'Envy' or manual installation to install previous drivers. You should remove those drivers before attempting to install using the built in tool. 

If your card does not appear in this list of cards known by Ubuntu 8.04 NVIDIA binary drivers (e.g. the 9600 GT) then there is no Ubuntu 8.04 provided binary driver. For unsupported workarounds try the links in See Also. 


Ubuntu 7.10 Gutsy Gibbon and Ubuntu 7.04 Feisty Fawn
For Ubuntu 7.10 and Ubuntu 7.04 the recommended way to install the binary drivers is to use System->Administration->Restricted Drivers Manager. This will try and automatically choose the correct driver version."

Did this resolve it? :)

Best Regards...


Okie ... pardon me but that is just simply too much information in one day for a Windows user >.<

I allready got the Graphics to work on best. so now graphic effects are working fine. However i was woundering how to actually get even more graphic effect.

Like for example, when you click on a drop down menu like "System" and then move your mouse to "Administration". the System menu will disapear but in a cool graphic way. like glitter or burn. Some kind of eye candy.

On another post, it was recomended to install "Compiz". and i specifically installed anything with "Compiz" in it.

Unfortunately, after the installation i looked and looked but couldnt find any icons for Compiz to play with the functions and options >.<

Regardless, Thanks a lot "ardvark71". i really do appreciate your time.

Kind regards,
Evil

---

### Post by ardvark71 on 2008-10-27
Hi...

Here is a graphical, step-by-step guide to get Compiz enabled. Don't worry that it says "Nvidia GeForce FX 5200," the author is using that particular card and has said that it should work with "all other Nvidia graphics cards." Also, if you enabled the restricted drivers, you can skip the first two sections and go to section 3, "Installing Compiz Fusion."...

[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)

Hope this helps! :)

Best Regards...

---

### Post by Evil79 on 2008-10-27
> **ardvark71 said:**
> Hi...

Here is a graphical, step-by-step guide to get Compiz enabled. Don't worry that it says "Nvidia GeForce FX 5200," the author is using that particular card and has said that it should work with "all other Nvidia graphics cards." Also, if you enabled the restricted drivers, you can skip the first two sections and go to section 3, "Installing Compiz Fusion."...

[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)

Hope this helps! :)

Best Regards...

Great !, that will help me alot, because iam still not used to Ubuntu that much. i always find my self looking for the "Start" button >.<

Once iam back from work ill look into this Compiz and try to install it to the fullest. because to be honest that is one of the main reasons i like Ubuntu. which is the great graphic effects.

Once again many thanks for your time "[COLOR="Red"]ardvark71[/COLOR]".

Kind regards,
Evil.

---

### Post by ardvark71 on 2008-10-27
> **Evil79 said:**
> 
Once again many thanks for your time "[COLOR="Red"]ardvark71[/COLOR]".


Hi...

You're most welcome, I'm glad I could help. :)

By the way, contrary to what you user name implies, I don't think you're as evil as you might think of yourself to be. ;) In our discussion thus far, you've shown respect and a great deal of gratitude. :)

These qualities are given to us by God, who IS and whose qualities, the Fruits of the Spirit, are inherant in Him. We don't exude them naturally. ;) See the link below for more details.

Thank you for treating myself and the others on your thread so kindly. :)

Best Regards...

---

### Post by Evil79 on 2008-10-27
> **ardvark71 said:**
> Hi...
You're most welcome, I'm glad I could help. :)
By the way, contrary to what you user name implies, I don't think you're as evil as you might think of yourself to be. ;) In our discussion thus far, you've shown respect and a great deal of gratitude. :)

My Dear Sir/Miss.

My nick name shows that iam "Evil", however being Evil does not mean that i should have no manners, or disrespect to those who help me and teach me.

During our discussion you and all of the members who replied to my posts respected me. Thus I return that respect.

> **ardvark71 said:**
> 
These qualities are given to us by God, who IS and whose qualities, the Fruits of the Spirit, are inherant in Him. We don't exude them naturally. ;) See the link below for more details.
Thank you for treating myself and the others on your thread so kindly. :)
Best Regards...

I respect your believes and i do respect you Sir/Miss. but Unfortunately iam an Atheist.

However iam still thankful for your kind words. And you are most welcome.

Kind regards,
Evil.

---

