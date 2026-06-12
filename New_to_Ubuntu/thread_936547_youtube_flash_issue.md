---
title: "youtube flash issue"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Ganonspike on 2008-10-02
i am now having sound failures, and mozzila shutdowns and am somewhat at a loss as to what to do.

---

### Post by mdszepher on 2008-10-02
If you can be more descriptive, it may help me or someone else with your problem.

Does the sound never play?  Does it cut out in the middle of a video into silence, or does it sound corrupted a few seconds in?

When Firefox shuts down, is it just on one video, a few, or all videos you try to play?

Also, what version of flash player did you install?  I think I had three choices for flash players, one being Adobe's player that I chose and the others being 3rd party.

Any other info you can include can never hurt, let us know about any patterns you find when you have problems.

---

### Post by Ganonspike on 2008-10-02
so far i did all the synaptic package removal of the mozzila plugins, then go all the sun-java6 installations except for the two you said you didnt. then copied the first piece of code. then tried to do the second but it failed here are the codes and instructions i used:



I'm assuming this is 8.04 Hardy Heron, if not don't do this!

I absolutely agree with using Synaptic to remove gnash. Just go to System > Administration > Synaptic Package Manager. Then type gnash in the search window, you'll see this:

Click image for larger version Name: Screenshot-Synaptic Package Manager .png Views: 5 Size: 60.4 KB ID: 87037

Make sure they're all "unticked".

Also while you're in synaptic make sure you have sun-java6-* installed. Just type sun-java6 in the search window and you'll see several sun-java6-*** packages. I install all EXCEPT sun-java6-doc & sun-java6-source.

Now, just yesterday I tried this with no other changes and it worked (I gave it a fairly rigorous test):

First remove flashplugin-nonfree either using synaptic or:

Code:

sudo apt-get remove --purge flashplugin-nonfree

If you've installed the flashplugin from any other source (tar.gz, .deb, etc.) do this in terminal:

Code:

cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so

NOTE: be patient, it may take a minute to run. You'll know it's done when you see the prompt:

Quote:
lance@lance-desktop:~$
Of course you're not Lance 


I did up to this point but the last code step failed when i tried, so i just ignored and went to the website and installed the flash pakage

please help thank you

---

### Post by kansasnoob on 2008-10-03
OK, since you're having sound and flash problems I'd follow the steps in my post #7 in this thread:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

But you emailed me about instructions from part of another instruction I gave, ie; I don't see lance@lance in the terminal.

I suspect you need some basic training regarding the terminal and synaptic. Now, I'm tired so don't expect much!

Start by looking here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Or let's just try a couple of simple commands. Go to terminal and:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

And then post the output of:

```
lsb_release -a
```

I need to know what version of Ubuntu you're using! I spent a few hours yesterday trying some things on a fresh Hardy install after testing a 8.10 Beta ISO and I thought the pulse audio stuff had been fixed in 8.04, but that was a two hour trial.

---

### Post by kansasnoob on 2008-10-03
> **Ganonspike said:**
> so far i did all the synaptic package removal of the mozzila plugins, then go all the sun-java6 installations except for the two you said you didnt. then copied the first piece of code. then tried to do the second but it failed here are the codes and instructions i used:



I'm assuming this is 8.04 Hardy Heron, if not don't do this!

I absolutely agree with using Synaptic to remove gnash. Just go to System > Administration > Synaptic Package Manager. Then type gnash in the search window, you'll see this:

Click image for larger version Name: Screenshot-Synaptic Package Manager .png Views: 5 Size: 60.4 KB ID: 87037

Make sure they're all "unticked".

Also while you're in synaptic make sure you have sun-java6-* installed. Just type sun-java6 in the search window and you'll see several sun-java6-*** packages. I install all EXCEPT sun-java6-doc & sun-java6-source.

Now, just yesterday I tried this with no other changes and it worked (I gave it a fairly rigorous test):

First remove flashplugin-nonfree either using synaptic or:

Code:

sudo apt-get remove --purge flashplugin-nonfree

If you've installed the flashplugin from any other source (tar.gz, .deb, etc.) do this in terminal:

Code:

cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so

NOTE: be patient, it may take a minute to run. You'll know it's done when you see the prompt:

Quote:
lance@lance-desktop:~$
Of course you're not Lance 


I did up to this point but the last code step failed when i tried, so i just ignored and went to the website and installed the flash pakage

please help thank you

Wait a minute. you're looking at post #9 here:

[http://ubuntuforums.org/showthread.php?t=936003](http://ubuntuforums.org/showthread.php?t=936003)

Pay attention!

"lance@lance-desktop:~$ " is a quote! It's not code!

But this is why I said to start your own specific thread. every problem can vary a little bit, as can the person you're dealing with.

---

### Post by Ganonspike on 2008-10-03
oh im usinmg ubuntu hardy 8.04, and yeah i know lance@lance or so is not what i want to put in terminal. my errocr occured at the step of code right before i was supposed to see lance@lance. The second piece of code ended in some error or so was the problem. ill look at post #7 and try that one now.

---

