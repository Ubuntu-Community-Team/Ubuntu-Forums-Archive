---
title: "Titan x vsync and cuda rendering issue ."
date: 2016-04-27
forum: New to Ubuntu
---

### Post by Tommy_Johnson_ on 2016-04-27
Just installed Ubuntu studio 16.04 and seems like I have no vsync " screen tearing on any fast moving image " and blender doesn't have the option for cuda rendering or even see my two titan x ,

I have tried compi, it shows vsync as enabled , I've tried nvidia settings , also shows vsync as enabled , I've tried a couple different Google results for file commands ext " all for trying to resolve the vsync issue .

I am new to Ubuntu and wonder if anyone with current nvidia has had this issue and knows a fix .

I do have the nvidia drivers from driver manager. And all software is up to date .

Pc specs if needed 
CPU: fx 9590
Ram: 32g 1866 adata
Mobo: asrock 990fx extreme 9
Gpus: sli evga titan x hydro coppers 
Psu: corsair ax1500i
Monitor: #1 benq bl3201ph , #2 asus vg248qe
Hdd for Ubuntu is a 4tb wb blue .

---

### Post by dino99 on 2016-04-27
maybe check the nvidia forum  for a better support  [https://devtalk.nvidia.com/](https://devtalk.nvidia.com/)

---

### Post by mcduck on 2016-04-27
I have no idea about the vsync issue, but might have some insight on Blender/CUDA...

Are you using the Blender version form Ubuntu's repositories, or the latest one from Blender website? Even though I'd usually recommend using software from Ubuntu's repositories when available, with Blender I'd definitely say get the version from the Blender website instead (You can just extract it somewhere in your home directory and run from there, so it's really easy and doesnt interfere with the rest of your system in any way). At least few years ago the package in Ubuntu's repositories didn't include certain things needed for CUDA support.

Also, you might need to install some extra packages from the repositories. libcuda is probably enough, but at least in 15.10 I needed cuda-toolkit as well. (I think I noticed the upgrade to 16.04 removing the cuda-toolkit, and GPU rendering is still working for me, so I assume just libcuda is enough now...)

---

### Post by Tommy_Johnson_ on 2016-04-27
For blender its the store 2.76a I believe " I'm currently at work and can't double check till I'm home " for older versions it appears I need an app called modprobe , not sure if still needed for 16.04 but will see , and for older versions a nvidia tool kit app , I'll check both those tonight .

---

### Post by Tommy_Johnson_ on 2016-04-27
Sorry, also the libcuda , forgot to mention

---

### Post by Tommy_Johnson_ on 2016-04-27
ok. libcuda is already installed with drivers , nvidia toolkit isnt avalible for kernal; 14.4 so both issues are still the same , forget blender for no I guess I can use that in winderp , but any ideas how to fix this screen tearing as it makes everything worthless .

---

### Post by oldrocker99 on 2016-04-27
Re:Blender

Steam has the latest version for free.

---

### Post by mcduck on 2016-04-28
I can't really think of any reason to install Blender through Steam, though, as the one you get from the website is literally just an archive you extract anywhere and run, without needing to install anything...

Also, all the requirements for using Cuda with Blender are definitely available in 16.04 (, so if I were you I wouldn't give up on it yet. I can alwaysa try to check what other related stuff I have installed. Do you have *nvidia-modprobe*? 

...and make sure to try the official version rather than the repositories version, they might not have been compiled with the same features (Cuda is proprietary stuff so I wouldn't be surprised if it's still disabled in Ubuntu version, at least it was some versions ago)

---

### Post by Tommy_Johnson_ on 2016-04-28
I did look for modprobe but had the same issue , didn't appear to be compatible with 16.04 , if I'm wrong please correct me , 

And for the official version, do you mean download the gpu drivers from nvidia directly and try, I did try adding a ppa and upgrade drivers to 364.19 but again was done so through a ppa .and yes I did purge the 361.xx drivers that Ubuntu  had installed .

---

### Post by mcduck on 2016-04-28
No, I mean getting the official version of Blender rather than installing it from Ubuntu's repositories. I'll check the cuda stuff I have installed bit later today when I have a chance.

---

### Post by Tommy_Johnson_ on 2016-04-28
you sir are awesome , i now have my cuda in blender , thank you very much .

any ideas on my vsync issue by chance ?

---

### Post by mcduck on 2016-04-29
Great, that's at least one issue sorted! Sadly I have no idea about the tearing issue, but I hope you find something... If you are feeling courageous, you could always try if getting the very latest driver from [this PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") helps.

---

### Post by Tommy_Johnson_ on 2016-04-29
Not sure if from that ppa , but I did use one and get 364.19 which appears to be latest driver

---

### Post by mc4man on 2016-04-29
I don't use xfce, (using compiz which 'assists' in vsync/no tearing) but a minor search on xfce(4) & vsync suggests that some install & enable compton, then disable or configure something in compton.
One thread, bottom posts  - [http://ubuntuforums.org/showthread.php?t=2212418](http://ubuntuforums.org/showthread.php?t=2212418)

---

### Post by Tommy_Johnson_ on 2016-04-29
ok, getting closer , if i enter either one of these two lines in terminal i get a single screen tear free but shuts off the other and overrides the screens settings , for example the dp-4 is for my 4k screen which i leave at 1920 x 1080 as the writing is too small to read at its native 3840 x 2160 resolution and then turns off my other display , so if any of you guys know how to write this and keep both monitors on , that should resolve the issue . here is the code 

nvidia-settings --assign CurrentMetaMode="DVI-I-1: nvidia-auto-select { ForceCompositionPipeline = On }"








nvidia-settings --assign CurrentMetaMode="DP-4: DVI-I-1 nvidia-auto-select { ForceCompositionPipeline = On }"

---

