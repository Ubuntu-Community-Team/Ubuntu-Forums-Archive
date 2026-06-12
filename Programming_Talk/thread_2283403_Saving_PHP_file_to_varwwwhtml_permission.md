---
title: "Saving PHP file to var/www/html permission"
date: 2015-06-21
forum: Programming Talk
---

### Post by nick198 on 2015-06-21
Hello everyone,

I just started out learning PHP but I don't have permission to save php files in the var/www/html folder. I've been searching in the forum but all I could find was how to save in the var/www/ folder, which now works fine. 

Would really appreciate any help!
Thanks a lot!
- Nick

---

### Post by flaymond on 2015-06-22
What do you mean by, 'I don't have permission' :-s? Do you mean you don't have the root access for it? If you have root access, just open terminal -> open any file manager with sudo/gksudo -> then just do your stuff. Anyway, I prefer using terminal to copy and moving file. :)

```
 sudo cp <input file> </to/directory/I/want> # copy the file you want to the directory
 sudo mv <input file> </to/directory/I/want> # move the file you want to the directory
``` 

I believe you have root access by the installed Apache.

# Remember always careful with sudo/root access, I once a long time ago erased the entire /boot and /bin directories of mine. That was an awful experience.

I'm thinking you are not an absolute beginner to Ubuntu or Linux. Anyway, it would be great if you provide more informations about your situation.

Cheers! ;)

---

### Post by nick198 on 2015-06-22
> **InterProg said:**
> What do you mean by, 'I don't have permission' :-s? Do you mean you don't have the root access for it? If you have root access, just open terminal -> open any file manager with sudo/gksudo -> then just do your stuff. Anyway, I prefer using terminal to copy and moving file. :)

```
 sudo cp <input file> </to/directory/I/want> # copy the file you want to the directory
 sudo mv <input file> </to/directory/I/want> # move the file you want to the directory
``` 

I believe you have root access by the installed Apache.

# Remember always careful with sudo/root access, I once a long time ago erased the entire /boot and /bin directories of mine. That was an awful experience.

I'm thinking you are not an absolute beginner to Ubuntu or Linux. Anyway, it would be great if you provide more informations about your situation.

Cheers! ;)

Thanks for your help. Yeah I mean that I don't have root permission. And I am an absolute beginner to Ubuntu :P

Well I'm not trying to save the files with the terminal. I open the text editor, type in the code and then I'm trying to save it as an .php file. 
Heres the screenshot:
 [IMG]https://scontent.xx.fbcdn.net/hphotos-xaf1/v/t1.0-9/11217955_1770182536542067_7607854352639009034_n.jpg?oh=b0ec903aa16ae73d01e2d35448134e27&oe=562469F6[/IMG]
Link: [http://bit.ly/1SCHwQz](http://bit.ly/1SCHwQz) 

Again, thank you so so much!:)

---

### Post by flaymond on 2015-06-22
Type ***sudo gedit *** to gain the root access for the php file you writing, write your code, then save it normally, then. If that you looking for.

Make sure you in var/html/www directory before editing or making the php, html, js, or whatever in the directory.


or

if you ***mean that you cannot use sudo because you don't have access for it either, don't have password or just cannot use it***, then I don't think that's possible to do that with easy way as far as I know, since it's a feature and is the reason nobody unwanted can't use your root access and system randomly.

Thanks, and welcome to Ubuntu community! Cheers! ;)

---

### Post by nick198 on 2015-06-23
> **InterProg said:**
> Type ***sudo gedit *** to gain the root access for the php file you writing, write your code, then save it normally, then. If that you looking for.

Make sure you in var/html/www directory before editing or making the php, html, js, or whatever in the directory.


or

if you ***mean that you cannot use sudo because you don't have access for it either, don't have password or just cannot use it***, then I don't think that's possible to do that with easy way as far as I know, since it's a feature and is the reason nobody unwanted can't use your root access and system randomly.

Thanks, and welcome to Ubuntu community! Cheers! ;)

Thanks it worked!:) Could you also tell me how to delete a specific file from that folder?:)
Thank you so much!

---

### Post by flaymond on 2015-06-23
If you using ubuntu, you might use ***nautilus*** as file manager. You can delete, move, rename file with root priviledge with ***sudo nautilus*** or any file manager you want to use with it (eg. ***sudo <your file manager>***).

or

If you want to delete from terminal, simply type this-

```
sudo rm <your file name>  # This will delete your file
```

Again, make sure you in the directory, that contain the  file you want to delete/erase and always careful when you use ***sudo***.

I also recommending you to have a look at this Linux Tutorial, to make your job easier (it will be hundred times handy if you a developer). - [http://linux-training.be/linuxfun.pdf](http://linux-training.be/linuxfun.pdf)

and please mark your thread as 'Solved', if you satisfied with the answers, by clicking the thread tools at top right of your thread.

Thanks and I'm glad it's working for you. ;)

---

