---
title: "Question about icons in apps."
date: 2019-03-06
forum: New to Ubuntu
---

### Post by dec56 on 2019-03-06
Good day, I am new to ubuntu and having trouble with the learning curve. I installed Wine so I could use DVD Flick and wouldn't work, so I uninstalled Wine and DVD Flick because neither one seemed to work but the Icons are still in the apps and I don't know how to delete them. 
 One other problem is if I try do do an update I get a message that it couldn't access the registry or something like that. I think I am going to like Ubuntu just have to get a little more understanding of it.  Any help will be appreciated!!

---

### Post by DuckHook on 2019-03-06
Welcome to the forums dec56, and welcome also to Ubuntu.

As a self-professed new user, here are a few suggestions you may wish to consider:

[LIST=1]
[*]Stay away from extras like WINE and Windows apps until you are more familiar with the base OS. The introduction of extraneous services and non-native apps can destabilize the system before you have had a chance to get used to it.
[*]There are many native Linux apps that are decent alternatives for the Windows apps you are used to. Give them a try. Falling back to Windows apps and WINE is generally a last resort tactic.
[*]Your update problems could be the result of uninstalling improperly.
[*]We need to see the actual output of your error messages before we can help. Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.
[*]How did you uninstall WINE and any apps? Please be precise and explain in detail.
[/LIST]
You may find the various links in my sig to be useful. Especially look over: ***Linux is Not Windows*** & ***Resources for Newcomers***. ***How to Ask for Help*** is also useful.

---

### Post by dec56 on 2019-03-06
I uninstalled Wine from the Ubuntu app center. I agree about the windows thing, and I am getting most things from Ubuntu apps, but the problem is the odd names they have for everything. I will copy that error message when I get a chance so people can see what it is. Like I said so far I like Ubuntu just takes time to get use to it. Thanks for the reply.

---

### Post by CatKiller on 2019-03-06
> **dec56 said:**
> I installed Wine so I could use DVD Flick and wouldn't work, so I uninstalled Wine and DVD Flick because neither one seemed to work but the Icons are still in the apps and I don't know how to delete them. 

They'll be in ~/.local/share/applications. The launchers are just text files.

---

### Post by dec56 on 2019-03-07
> **CatKiller said:**
> They'll be in ~/.local/share/applications. The launchers are just text files.
 That was easy! Worked great, Thank You..

---

