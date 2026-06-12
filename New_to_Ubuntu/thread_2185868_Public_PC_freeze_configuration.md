---
title: "Public PC freeze configuration"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by wcdubois on 2013-11-04
I am changing our public use PCs from XP Pro to Ubuntu 12.04 and would like to be able to reset them to their new pristine install condition daily.
Is there a setting or application that will accomplish this for me with a daily power restart?
I wan to be able to automatically remove everything that the users have done on the PC.

Thanks!

---

### Post by newb85 on 2013-11-04
Look over this:  [http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS)

It looks like the instructions were set up in some sort of Gnome-fallback session.

You may find that Xubuntu is better suited for the task, especially if the machines were originally XP machines (meaning probably somewhat older hardware).  Lubuntu is even lighter, but Lubuntu 12.04 isn't LTS.

Edit: on second glance, it looks like the instructions were created in Lucid or Maverick.  If you hit any barriers, post them.

---

### Post by sandyd on 2013-11-04
> **wcdubois said:**
> I am changing our public use PCs from XP Pro to Ubuntu 12.04 and would like to be able to reset them to their new pristine install condition daily.
Is there a setting or application that will accomplish this for me with a daily power restart?
I wan to be able to automatically remove everything that the users have done on the PC.

Thanks!
Yes - just use the guest account 

It will not allow users to change system settings/etc, but allow users to access applications/internet on the computer.
After they log off the guest account, the account is reset.

---

### Post by wcdubois on 2013-11-08
Ah yes, Kiosk mode is the phrase I was looking for.
After reading and mostly understanding the instructable, it sure seems like the simplicity of using the guest account is the best way to go.
Is there any down side to using the guest account to make a kiosk PC?

Thanks

---

### Post by grahammechanical on 2013-11-08
You will have to hide the admin user name from the log in screen to avoid temptation. So that only the guest account is available. This might help you do that.

[http://askubuntu.com/questions/163457/how-to-hide-users-from-the-user-account-list-of-the-login-screen-in-ubuntu-12-10](http://askubuntu.com/questions/163457/how-to-hide-users-from-the-user-account-list-of-the-login-screen-in-ubuntu-12-10)

And this might help you make the guest account an automatic login account. 

[http://askubuntu.com/questions/95405/how-to-enable-guest-account-automatic-login](http://askubuntu.com/questions/95405/how-to-enable-guest-account-automatic-login)

One or the other or both might be useful. It does occur to me that with the guest account on automatic login that there may be difficulties logging in as administrator for administrative tasks. So, I suggest that you become familiar with editing system files from Recovery Mode. So, that at the very least you can remove automatic login for the guest account.

At the Recovery menu selecting Network will not only set up an internet connection (might be needed for running updates) but it also puts the file system into read/write mode which is necessary for when you then select Root shell prompt to do the editing. Nano is an installed text editor that runs from the command line.

Regards.

---

### Post by newb85 on 2013-11-09
If you set the machines up for automatic guest login per grahammechanical's second link, there are still ways to accomplish administrative tasks.

You could install openssh-server on the machines so that you can ssh into them.  A lot of administrative tasks can be handled through the CLI and can be managed that way.

Then, you could create two different versions of /etc/lightdm/lightdm.conf (one with automatic guest login and one without) which you store somewhere else.  Then, you could create two shell scripts that copy one or the other to /etc/lightdm/lightdm.conf.  That way, for non-CLI admin tasks, you could ssh in and run the shell script disabling automatic guest login.

---

