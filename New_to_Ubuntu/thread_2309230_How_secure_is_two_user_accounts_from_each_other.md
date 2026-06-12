---
title: "How secure is two user accounts from each other?"
date: 2016-01-08
forum: New to Ubuntu
---

### Post by Tobias_Sund on 2016-01-08
Hi,

I've recently switch over to linux from windows and is pleasantly surprised so far! The switch has also made me more into security and right now I&#8217;m trying to strike a good balance between security and usability. I know that Linux is more secure than windows right off the bat but I want to go further. And most of all, I want to feel that I have a reasonable understanding of the different aspects that surrounds security.

So my goal is to make a secure environment that doesn&#8217;t involve to much hassle in the day-to-day use. And I&#8217;m wondering if a solution involving multiple user accounts could fit my needs. My starting point was as follows; one computer, two users (in reality these users are one and the same; me). One user only browses the web, and thus want access to his/hers bookmarks and so forth. This user doesn&#8217;t know anything about security and clicks on everything that seams interesting (potentially malicious). The other user handles sensitive information and mostly connects to other computers over ssh etc.

Is it possible to let these two individuals use the same computer (not at the same time of course) but with two different accounts and still ensure that any web browser related actions that user one makes doesn&#8217;t compromises user twos need of a secure environment? I have an idea of how to make this happen but I don&#8217;t know if it&#8217;s possible to do.

As already stated two user accounts; one &#8220;browser account&#8221; and one &#8220;secure account&#8221;. 

(1)  The &#8220;browser account&#8221; can&#8217;t change anything, install new apps etc. (should be able to open pdf:s in the browser though). Is this possible?

(2)  Only an outside account can change the installed apps that the &#8220;browser account&#8221; can use. Same goes for updating already installed apps. Possible?

(3)  Every time that the &#8220;browser account&#8221; gets logged off the state of the accounts gets reset, downloaded files and any changes what so ever gets deleted. Possible? (the start state can only be changed by the account that can install new apps for the user)

If 1, 2 and 3 is possible, it should make it harder for any potential malicious code to infect the system. Correct?

If the system gets infected anyway, is there still a great risk that the secure account also will be affected?

I have tried to read about user privileges and so forth but thus far I haven&#8217;t found any answer to my questions, I&#8217;m probably using the wrong words when searching.

I am using ubuntu 15.10 btw.

/Tobias

---

### Post by sandyd on 2016-01-08
> **Tobias_Sund said:**
> Hi,

I've recently switch over to linux from windows and is pleasantly surprised so far! The switch has also made me more into security and right now I&#8217;m trying to strike a good balance between security and usability. I know that Linux is more secure than windows right off the bat but I want to go further. And most of all, I want to feel that I have a reasonable understanding of the different aspects that surrounds security.

So my goal is to make a secure environment that doesn&#8217;t involve to much hassle in the day-to-day use. And I&#8217;m wondering if a solution involving multiple user accounts could fit my needs. My starting point was as follows; one computer, two users (in reality these users are one and the same; me). One user only browses the web, and thus want access to his/hers bookmarks and so forth. This user doesn&#8217;t know anything about security and clicks on everything that seams interesting (potentially malicious). The other user handles sensitive information and mostly connects to other computers over ssh etc.

Is it possible to let these two individuals use the same computer (not at the same time of course) but with two different accounts and still ensure that any web browser related actions that user one makes doesn&#8217;t compromises user twos need of a secure environment? I have an idea of how to make this happen but I don&#8217;t know if it&#8217;s possible to do.

As already stated two user accounts; one &#8220;browser account&#8221; and one &#8220;secure account&#8221;. 

(1)  The &#8220;browser account&#8221; can&#8217;t change anything, install new apps etc. (should be able to open pdf:s in the browser though). Is this possible?

(2)  Only an outside account can change the installed apps that the &#8220;browser account&#8221; can use. Same goes for updating already installed apps. Possible?

(3)  Every time that the &#8220;browser account&#8221; gets logged off the state of the accounts gets reset, downloaded files and any changes what so ever gets deleted. Possible? (the start state can only be changed by the account that can install new apps for the user)

If 1, 2 and 3 is possible, it should make it harder for any potential malicious code to infect the system. Correct?

If the system gets infected anyway, is there still a great risk that the secure account also will be affected?

I have tried to read about user privileges and so forth but thus far I haven&#8217;t found any answer to my questions, I&#8217;m probably using the wrong words when searching.

I am using ubuntu 15.10 btw.

/Tobias
If you want, you can just use the guest account.

It will allow browser access (along with everything installed), but not allow you to install apps and only save files until logoff.

That being said, by default, Ubuntu's file permissions prevent one user from accessing another user's home folder, so what you do in one account as the account user should not affect the other. That excludes the usage of sudo, su, pkexec, or tool to escalate the user's privileges.

---

### Post by coldraven on 2016-01-09
IMO the weakest link in Ubuntu is Adobe Flash. You could remove it, YouTube will still work, or set it to "Ask to activate". This will stop any Flash based advertising that contain malware. To do that in Firefox go to Tools>Add-ons and set the Shockwave Flash option.
There are also many Firefox plug-ins that help your online security and privacy.
Ghostery, prevents trackers.
AdBlockPlus or uBlock Origin , prevents most adverts.
BetterPrivacy, deletes Flash cookies. (which some companies use to track you)
NoScript, blocks Java script (you only allow Java script on sites that you trust)

Happy browsing, it's a mad bad world out there :)

---

### Post by kurt18947 on 2016-01-09
The use of add-ons can enhance the browsing experience and secuity. Too many add-ons can cause some web sites to not function as expected. I had trouble with ghostery when used with noscript and adblock plus. I've replaced adblock plus with Bluhell Firewall which seems to cause fewer issues but still limits undesirables.

---

### Post by Tobias_Sund on 2016-01-09
> **sandyd said:**
> If you want, you can just use the guest account.

It will allow browser access (along with everything installed), but not allow you to install apps and only save files until logoff.

That being said, by default, Ubuntu's file permissions prevent one user from accessing another user's home folder, so what you do in one account as the account user should not affect the other. That excludes the usage of sudo, su, pkexec, or tool to escalate the user's privileges.

Interesting tip! But with a guest account I need to sign in to sync my bookmarks every time upon login, right? (not that much of a hassle but anyway)

If I understand everything you can't use sudo etc. in a guest account so that's an additional bonus! I think it is possible to restrict an "ordinary" user account from using sudo etc. as well, is that correct? 

So now if I use a guest account, is it still a possibility that the guest account can get infected? If so, can this infection then spread to the secure account and affect the rest of the system? I know you can't be 100% secure, due to bugs and potential exploits in the code, but if we limit [FONT=Verdana]ourselves[/FONT] to the human factor and "ordinary" malicious code, are we reasonable safe? Maybe I should refrase my question; Can a guest account change any system-wide data? If not, we would be quite safe right? Or let me but it this way; Would YOU be ok with letting a user that have no understanding of safety use a guest account on the same computer with which you do some security critical tasks?

> **coldraven said:**
> IMO the weakest link in Ubuntu is Adobe Flash. You could remove it, YouTube will still work, or set it to "Ask to activate". This will stop any Flash based advertising that contain malware. To do that in Firefox go to Tools>Add-ons and set the Shockwave Flash option.
There are also many Firefox plug-ins that help your online security and privacy.
Ghostery, prevents trackers.
AdBlockPlus or uBlock Origin , prevents most adverts.
BetterPrivacy, deletes Flash cookies. (which some companies use to track you)
NoScript, blocks Java script (you only allow Java script on sites that you trust)

Happy browsing, it's a mad bad world out there :)

> **kurt18947 said:**
> The use of add-ons can enhance the browsing experience and secuity. Too many add-ons can cause some web sites to not function as expected. I had trouble with ghostery when used with noscript and adblock plus. I've replaced adblock plus with Bluhell Firewall which seems to cause fewer issues but still limits undesirables.

Have already disabled Adobe Flash and I'm using AdBlock and something called PrivacyBadger,  I will check out the other plug-ins though :) Thanks guys!

---

### Post by DuckHook on 2016-01-09
In my opinion, you are making things too difficult for yourself, which both diminishes from the user experience and makes your computing life unnecessarily complicated.

Let's start from your end goal first and then find a solution that works.

Your desire is to surf unknown sites that concern you due to their questionable nature. So, what you really want is to sandbox your browser so that anything that happens to your browser cannot possibly affect the rest of your system. Moreover, if you could easily undo any damage that was done to your browser, and do it in a way that is guaranteed to get rid of any malware, this would be a big bonus.

If this description is accurate, then the best solution for you is to run another 'buntu in a Virtual Machine. I would highly recommend Lubuntu for this task because it is lightweight and responsive, which are critical properties once you introduce the overhead of a VM.

You can try out VirtualBox, which is available from the repositories. VM technology basically runs a make-believe computer inside a window on your real computer. You can load up this make-believe computer with any compatible operating system. The result is a computer within a computer. The make-believe computer is basically sandboxed within its own walled jail and cannot affect the workings of your real computer (unless you make silly modifications to the default install that break the jail walls). Additionally, the technology allows you to take a snapshot of the make-believe computer at any time and revert to it in case of trouble. In your case, you would take a snapshot of the system right after installation. Any time that subsequent surfing creates any concerns, you wouldn't have to do anything at all except revert to your snapshot. It would be like stepping back in time. It's the closest thing we have to worry-free computing.

Among the many advantages, a key one is that you could have your browser running inside the VM while you are getting stuff done on your real machine at the same time. In fact, you could have your "real" browser browsing a safe and trusted site *at the same time* that your sandboxed VM browser is surfing elsewhere. No having to log out, then in to a different account; no interruption in your work flow.

Setting up a VM is not especially difficult. The people on this forum can help you through the process.

The biggest drawback to running VMs is that you need decent hardware to run one well. We don't know your HW, so give us some idea of your specs.

PS, the other security measures mentioned in this thread are still important for your main browser.

---

### Post by sandyd on 2016-01-09
> **Tobias_Sund said:**
> Interesting tip! But with a guest account I need to sign in to sync my bookmarks every time upon login, right? (not that much of a hassle but anyway)

If I understand everything you can't use sudo etc. in a guest account so that's an additional bonus! I think it is possible to restrict an "ordinary" user account from using sudo etc. as well, is that correct? 

So now if I use a guest account, is it still a possibility that the guest account can get infected? If so, can this infection then spread to the secure account and affect the rest of the system? I know you can't be 100% secure, due to bugs and potential exploits in the code, but if we limit [FONT=Verdana]ourselves[/FONT] to the human factor and "ordinary" malicious code, are we reasonable safe? Maybe I should refrase my question; Can a guest account change any system-wide data? If not, we would be quite safe right? Or let me but it this way; Would YOU be ok with letting a user that have no understanding of safety use a guest account on the same computer with which you do some security critical tasks?


No, a guest account cannot change system data.

That being said, I am on the paranoid side, and simply don't let anyone else use my computer for whatever reason.

Duckhook has a point though, VMs are another good possibility.

You can simply either

a) Just don't install Ubuntu, run Ubuntu via Live media in the VM
b) Install Ubuntu, create a snapshot, and keep on coming back to the snapshot when starting up.

---

