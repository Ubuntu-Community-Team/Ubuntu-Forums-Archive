---
title: "[SOLVED] Firefox goes grey / gray colour / color"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by stinger30au on 2008-05-05
i have noticed that every now and then when im scrolling down a web page that firefox will go a grey colour, sometimes the colours will return but other times its like viewing the web thru an old black and white telly.

in using 8.04 and firebox 3 beta 5 i installed from the repos

thanks for reading

---

### Post by Trail on 2008-05-05
Do you have compiz enabled?

This is probably a compiz plugin that fades a window to gray if that application becomes non-responsive.

---

### Post by Jongleur on 2008-05-05
I've got the same problem. Can you explain what this code does please?

---

### Post by omns on 2008-05-05
> **Jongleur said:**
> I've got the same problem. Can you explain what this code does please?

it's 
> **Trail said:**
> 
... a compiz plugin that fades a window to gray if that application becomes non-responsive.

---

### Post by Jongleur on 2008-05-05
Thanks for the really helpful reply.

---

### Post by omns on 2008-05-05
Do you mean 

banner -w 50 Trail?

that is just Trail's signature

---

### Post by Jongleur on 2008-05-05
Ah, right. Very strange sig. Thanks.

Any idea how to stop Compiz doing this?

---

### Post by omns on 2008-05-05
You could turn off Visual effects altogether in System-->Preferences-->Appearance-->Visual Effects

If you want compiz to remain then I'm not sure which plugin handles this effect. I don't mind it as it tells me that my system is working hard and needs a chance to recover for a few seconds.

---

### Post by Jongleur on 2008-05-05
Thanks. Now that WAS helpful!

---

### Post by stinger30au on 2008-05-05
> **Trail said:**
> Do you have compiz enabled?

This is probably a compiz plugin that fades a window to gray if that application becomes non-responsive.

yes i do have compiz enabled. i have since disabled it and now it has stopped happeing...well the greyness any how.
i will try and install firefox 2 from the repos and see if that makes any difference to the web browser locking up as well.
will report back my findings asap
thanks for the info

---

### Post by Jongleur on 2008-05-05
It's not only Firefox that's affected, it happens in Opera too.
(And sorry for hijacking your thread)

---

### Post by stinger30au on 2008-05-05
ok, i have installed firefox 2 from the repos and have only been ising it for a few minutes and already i can see a *HUGE* speed increase by using it instead FF3.

i will stick to FF2 for a while longer i think.

---

### Post by billgoldberg on 2008-05-05
> **stinger30au said:**
> ok, i have installed firefox 2 from the repos and have only been ising it for a few minutes and already i can see a *HUGE* speed increase by using it instead FF3.

i will stick to FF2 for a while longer i think.

Strange because ff3 is much faster than ff2.

[http://www.thebrowserworld.com/2008/03/29/firefox-30-beta-4-vs-opera-950-beta-vs-safari-31-beta-multiple-sites-opening-test/](http://www.thebrowserworld.com/2008/03/29/firefox-30-beta-4-vs-opera-950-beta-vs-safari-31-beta-multiple-sites-opening-test/)

If a application "grays out" it means it is not responding.

Some times you can just wait a few seconds and everything will be fine (synaptic does this a lot) but it could also mean the application has crashed.

---

### Post by Trail on 2008-05-05
Heh, sorry about my sig, it's lame but I'm lazy about changing it.

If you execute the code in my sig, it prints:
```

                                       ######
                                        ######
                                           ###
                                            ##
                                             #
            #                                #
            #                                #
            ##################################
            ##################################
            ##################################
            #                                #
            #                                #
                                             #
                                            ##
                                            ##
                                        ######
                                        ######
            #                  #
            ####################
            ####################
            ####################
            #             ###
                            ##
                             ##
                             ###
                         #######
                         #######
                         #######

                ###
              ########
             ##########   #####
            ####    ####  ######
            ##        ##      ##
            ##        ##       #
             ##      ##       ##
              ##################
            ###################
            ##################
            ##
            #
            #                  #
            ####################      ###
            ####################     #####
            ####################     #####
            #
            #                                #
            ##################################
            ##################################
            ##################################
            #

```

---

### Post by freesitebuilder on 2008-05-05
I have found that certain websites tie up Fx3 and cause it to stop responding, sometimes for a few seconds, sometimes I have to force quit. One that I know often causes problems is my local papers site.

---

### Post by Bigtime_Scrub on 2008-05-05
> **freesitebuilder said:**
> I have found that certain websites tie up Fx3 and cause it to stop responding, sometimes for a few seconds, sometimes I have to force quit. One that I know often causes problems is my local papers site.

Ive had this problem too but I thought I just had a bad internet connection.

So from what Ive heard I can change to Firefox 2 or turn off compiz.

Any other suggestions?

---

### Post by stinger30au on 2008-05-05
> **Bigtime_Scrub said:**
> Ive had this problem too but I thought I just had a bad internet connection.

So from what Ive heard I can change to Firefox 2 or turn off compiz.

Any other suggestions?

yes, turn off compiz *AND* install FF2

im amazed at how slow FF3 runs on my pc... mind numblingly slow...  FF2 looks like a rocket

---

### Post by shazbut on 2008-05-05
For me this problem usually only occurs on web pages the use flash.  So it's probably the flashplugin at fault (again).  I wish designers would stop making web pages that rely on this horrible binary blob to work, it adds nothing to the usefulness of a site.

---

### Post by stinger30au on 2008-05-06
> **Trail said:**
> Heh, sorry about my sig, it's lame but I'm lazy about changing it.

If you execute the code in my sig, it prints:
```

                                       ######
                                        ######
                                           ###
                                            ##
                                             #
            #                                #
            #                                #
            ##################################
            ##################################
            ##################################
            #                                #
            #                                #
                                             #
                                            ##
                                            ##
                                        ######
                                        ######
            #                  #
            ####################
            ####################
            ####################
            #             ###
                            ##
                             ##
                             ###
                         #######
                         #######
                         #######

                ###
              ########
             ##########   #####
            ####    ####  ######
            ##        ##      ##
            ##        ##       #
             ##      ##       ##
              ##################
            ###################
            ##################
            ##
            #
            #                  #
            ####################      ###
            ####################     #####
            ####################     #####
            #
            #                                #
            ##################################
            ##################################
            ##################################
            #

```

learn something new every day.... thanks for sharing

---

### Post by philinux on 2008-05-06
FF3 is still beta. However I find it fast and it's only using 133meg of ram.

Workarounds.

1. Get the flashblock addon that replaces flash with an "f" icon and then you can play the ones you want.

2. See attached screen print and uncheck the "Tell me if a website.... options.

---

### Post by omns on 2008-05-09
> **philinux said:**
> FF3 is still beta. However I find it fast and it's only using 133meg of ram.

Workarounds.

1. Get the flashblock addon that replaces flash with an "f" icon and then you can play the ones you want.

2. See attached screen print and uncheck the "Tell me if a website.... options.

I've found that adblock and flashblock slow down my low spec machine considerably and increase the greyed out effect.

---

### Post by omns on 2008-05-18
I've recently dumped Ubuntu's Firefox 3 beta 5 for the latest nightly builds from Mozilla and am seeing much improved performance. No grey outs at all :)

---

### Post by stinger30au on 2008-05-18
i was reading here in the forums yesterday that firefox 3 has came out with a RC-1 fingers crossed it his the repos in a few days

---

### Post by Sef on 2008-05-18
Should be in within a week.

---

