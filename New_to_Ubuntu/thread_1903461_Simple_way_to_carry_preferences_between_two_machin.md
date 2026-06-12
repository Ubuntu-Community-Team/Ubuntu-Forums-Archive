---
title: "Simple way to carry preferences between two machines?"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-01-02
I THINK that is what I am talking about anyway! :oops: What I mean is, I have just set up one of my laptops to run Xubuntu 11.10 and having got all the twiddles and software just right I would like to carry all that over to the other laptop I have to sort out. Can anyone give me any ideas? (and nice simple ones too ... I am not too good in the terminal or shifting things around in my home folder ...) :D

---

### Post by ajgreeny on 2012-01-02
You will simply need to copy all the contents of the home folder, including all the hidden files and folders from the old machine to the new one, and put them in /home/user again, just the same as they came from.

If you have the same username on both machines it should all work out of the box, but depending on how you make the move of the files, if you have a different username you may need to use ```
sudo chown -R $USER:$USER /home/$USER
```to give ownership of the files and folders to the new name.

This will not give you all the installed packages you have added since installation, which you will need to install again on the new machine, but tom save bandwidth you can copy all the packages in /var/cache/apt/archives on the old machine to the new one, then use synaptic or apt-get (or software-center, which I don't use myself) to install the same packages as on the old machine.

---

### Post by LewisTM on 2012-01-02
The Software Center has a feature to synchronize installed packages between machines. All you need is a Ubuntu One account.

Then synching the hidden directories in your Home will copy application and desktop preferences.

You might need to hunt down system settings that are configured by the superuser like printing and networking. For instance synching /etc/cups should replicate your printer settings. 

Cheers!

Edit: Not sure if the Software Center in Maverick has the feature mentionned above.

---

### Post by hamstermoon on 2012-01-03
I will have a bash at doing that. I am running Xubuntu Oneric on the Laptop and want to sync that with another that will be running Oneric in the very near future. I'll report back!

---

### Post by mapes12 on 2012-01-03
I haven't used it in a while but [Remastersys]("http://www.geekconnection.org/remastersys/index.html") will create an installation CD to mirror your current setup that you can install on other machines.

):P

EDIT:Not sure if it's what you're after but [AptonCD]("http://aptoncd.sourceforge.net/") is also useful.

---

### Post by hamstermoon on 2012-01-04
I tried Aptoncd but unfortunately that fell by the wayside when I realised that the notebook I was setting up didn't have an internal cd drive. The program wouldn't recognise the external one I use. 
 
Anyway, I just gave in and did an install from scratch. It only took me a couple of hours and I am now set up and happy.

---

### Post by hamstermoon on 2012-01-04
LewisTM - I will need more instuctions about how to do what you are saying. I had a look and didn't know what I was looking for! Can you point me to the package??

---

### Post by LewisTM on 2012-01-04
> **hamstermoon said:**
> LewisTM - I will need more instuctions about how to do what you are saying. I had a look and didn't know what I was looking for! Can you point me to the package??

Just select 'File/Sync Between Computers' in the Software center and follow the instructions.
A guide [here]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/").

---

