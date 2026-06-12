---
title: "Running sudo from inside a bash script"
date: 2010-05-31
forum: Programming Talk
---

### Post by vamega on 2010-05-31
Hi.

I was wondering if it is possible to run a command like
```
sudo <command> <arguments>
``` in a bash script.

Will the shell just prompt the user for the password when this comes up?

Thanks in advance.

Vamega.

---

### Post by dwhitney67 on 2010-05-31
> **vamega said:**
> 
Will the shell just prompt the user for the password when this comes up?

Why not just write a small script and find out for yourself?

If you really need my opinion, I would **not** insert the 'sudo' within the script; just run the script itself using sudo.

---

### Post by nvteighen on 2010-05-31
> **vamega said:**
> Hi.

I was wondering if it is possible to run a command like
```
sudo <command> <arguments>
``` in a bash script.

Will the shell just prompt the user for the password when this comes up?

Thanks in advance.

Vamega.

You can and it will prompt for the password... if and only if the timeout has passed.

What I mean is that using sudo inside your script makes it possible to be run as root without asking the user's password in certain occasions like having used sudo before (Ubuntu's default, IIRC, uses a 10-min timeout for non-prompted sudo). That's a really bad idea... ok, maybe the whole sudo idea is a bad one, but I won't get into the su vs. sudo wars... The thing is that the best decision is always the one that gives control to the user, so that he decides to run your script as root or not by making him write "sudo" or not... that way, even if the timeout hasn't passed yet, the user will know that the script will be running as root.

Another reason for not using sudo inside a script is compatibility. Lots of people don't use sudo, but su, su-to-root (a nice idea) or they just login as root. By not using sudo or su in your script, you allow the user to decide how he gets root privileges. Keep in mind that e.g. Debian uses su as its default, not sudo.

---

### Post by vamega on 2010-06-02
Well the scrpit I'm writing is most certainly tailored to ubuntu at the moment.
It uses tasksel, and expects things to be places where they are placed in ubuntu.

Is there any way I can force sudo to ask for a password, or force the timeout to pass?

Thanks

Vamega

---

### Post by sisco311 on 2010-06-02
> **vamega said:**
> Well the scrpit I'm writing is most certainly tailored to ubuntu at the moment.
It uses tasksel, and expects things to be places where they are placed in ubuntu.

Is there any way I can force sudo to ask for a password, or force the timeout to pass?

Thanks

Vamega

```
sudo -k comamnd
```
See **man sudo** for details.

---

### Post by nvteighen on 2010-06-02
It still is a bad idea: an Ubuntu user could have deinstalled/deactivated sudo if he wanted. 

Moreover, you're deciding to make your script inherit all possible vulnerabilities (known and unknown). By making the user decide how to gain root privileges you give him freedom of choice. Basically, it all boils down to a modularity issue, where using sudo that way breaks it by reducing your script's interfacing capabilities in a place that's critical, at least to me.

---

### Post by vamega on 2010-06-07
I don't want most of the commands the script runs tot run as root.
Just two commands in the script.

How would I implement this without choosing which utility is used (sudo|su|something else)

---

### Post by StephenF on 2010-06-08
> **vamega said:**
> I don't want most of the commands the script runs tot run as root.
Just two commands in the script.

How would I implement this without choosing which utility is used (sudo|su|something else)
Consider using a bash subshell (any code in parentheses()). You can "su username" in the subshells and when the subshell ends you should be back as root. The su command does not ask for or require a password when running as root.

The disadvantage of this approach is that it requires a specific username to remain on the system.

If all you need root for is to access or modify certain files a better approach would be to give your user the necessary group permissions to do so.

---

