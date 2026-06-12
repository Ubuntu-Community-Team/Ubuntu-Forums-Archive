---
title: "Change password"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by zebmustafa2010 on 2013-11-21
Hello every one ,

I am new user of ubuntu and  I am currently installing ubuntu 13.04 on my  system. I want to change my previous password with the new one. What i  do for it.          
Help?


Regards

Zeb Mustafa

---

### Post by lisati on 2013-11-21
Are you referring to your forum password or your computer's password?

If you're referring to your computer's password and you are doing a clean install, one would expect that you are given an option to put in your choice of new password during installation.

---

### Post by zebmustafa2010 on 2013-11-22
De**ar **lisati

I am actually refering to my computer password .
When I go in > **System Setting** > **User Account**
 click on the **password** field and dialog box appear for changing password 
After filling all the filed the button** change** stil hidden.
I don't understand why change button is hidden?

---

### Post by coffeecat on 2013-11-22
Not a Forum Feedback & Help thread.

*Thread moved to **Absolute Beginners Section**.*

---

### Post by heir4c on 2013-11-22
> **zebmustafa2010 said:**
> De**ar **lisati

I am actually refering to my computer password .
When I go in > **System Setting** > **User Account**
 click on the **password** field and dialog box appear for changing password 
After filling all the filed the button** change** stil hidden.
I don't understand why change button is hidden?



I open it to help you and I type my password in and than type a new one in the 2 field, than it still be hidden like you say. When you click on the gear at the right in the text-field, than he produces a password and than you can change it as well. 
But !!!!! If you click on "View password" (or something like that in English, I have a Dutch version) than you see that is a to difficult password to remember.

So, what you must do, if you don't want that, is:
Open a terminal (You can find that via the Dash or via keycombination: Ctrl+Alt+T) and type:
```
sudo -i
```
and click Enter. Type your password, you will not see what you typing now, but that is normal, that's for safety. Click Enter after you type your password.
Now you act like root.
Type in:
```
passwd username
```
Of course you change 'username' in your real username. (I your username is john than you type: passwd john )
Click Enter.
Than type the new password, here you can choose what you want, click Enter
Than type it again en click Enter;
That's all you have to do.

---

### Post by Impavidus on 2013-11-22
If you can login and want to change your own password using the terminal you don't need sudo. Ordinary users have the right to change their password (obviously). Just give the command **passwd** and follow the instructions. Keep in mind that when typing passwords in the terminal no characters are shown. You can use the graphical interface, but that changes with every flavour and release. The command line interface hasn't changed in ages.

---

### Post by zebmustafa2010 on 2013-11-23
When I click on the gear at right on the text field  it automatically generate the password but still the change button is hidden.
I did this successfully through terminal but **how I come back to my previous position like "zeb@zeb-lenovo-B570:~$" from root position?**

I got the problem!
when I give password of  eight length than **change** button is still hidden and when I exceed the password length , automatically **change** button is unhidden and I easily change my password by clicking on **change** button.

---

### Post by heir4c on 2013-11-23
> how I come back to my previous position like "zeb@zeb-lenovo-B570:~$" from root position?
type:
```
exit
```

> I got the problem!
when I give password of eight length than change button is still hidden and when I exceed the password length , automatically change button is unhidden and I easily change my password by clicking on change button. 

Ok!
I think I did not notice that when I try it out before, But now I see it. ThanX.

---

### Post by zebmustafa2010 on 2013-11-23
Got it,
Thank you

---

