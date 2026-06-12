---
title: "sudo apt get problems"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by kiwi-pete on 2008-08-30
here is the error I encounter when trying to update my system. This is derived from problems with update manager so I thought id try the terminal to update. I have version 8.04.1

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>

W: GPG error: [http://falcon.landure.fr](http://falcon.landure.fr) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CA3E3239FA7DC39
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release](http://wine.budgetdedicated.com/apt/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
kiwipete@Ubuntu-laptop:~$ 

If I run the apt get again, it is the same error.
What's happening here please?

---

### Post by nothingspecial on 2008-08-30
> **kiwi-pete said:**
> 
W: You may want to run apt-get update to correct these problems


The answer might be in the question.

---

### Post by nothingspecial on 2008-08-30
Sorry, that wasn`t very "absolute beginner"

The terminal is telling you to run
```
apt-get update
``` to correct the problem.

You have to sudo it
```
sudo apt-get update
```

If this doesn`t may be that you need a key for the wine repository. 

***Disclaimer*** Have never used wine.

See here for further instructions on adding the key -
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by kiwi-pete on 2008-08-30
> **nothingspecial said:**
> Sorry, that wasn`t very "absolute beginner"

The terminal is telling you to run
```
apt-get update
``` to correct the problem.

You have to sudo it
```
sudo apt-get update
```

If this doesn`t may be that you need a key for the wine repository. 

***Disclaimer*** Have never used wine.

See here for further instructions on adding the key -
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I did sudo it, but the error is still the same.

I will go and look at the URL you posted, thanks.

---

### Post by kiwi-pete on 2008-09-06
Ok, so I have come up against a wall here, I still get this error.

[I]W: GPG error: [http://falcon.landure.fr](http://falcon.landure.fr) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1CA3E3239FA7DC39
W: You may want to run apt-get update to correct these problems[/I]

I have run and re-run sudo apt-get update without any sign of improvement here.
I have looked at the above site and am even more confused.

Can anyone please help me to get around this error?

---

### Post by ad_267 on 2008-09-06
That looks like just a warning, not an error. You should still be able to update. And I don't think it's going to go away with updating, it's probably because the repositories you're using aren't official ones.

---

### Post by kiwi-pete on 2008-09-06
So I needent worry then?
Is there any way of deleting it, or should I leave it be?

---

### Post by ad_267 on 2008-09-06
Well as long as you can still get updates and install stuff it should be fine. You can delete those lines from your sources.list file if you don't need them but I'm guessing you added them so you could install some particular application and might want to get updates for that.

---

### Post by cwsnyder on 2008-09-06
What I am reading is that one of your Wine application repositories at Wine.hq got corrupted.  Possibly written by someone not authorized to update the repository for the /falcon/landure.fr package.  I would try again in a few days to see if it were corrected.  You may also want to report to the [www.winehq.com](www.winehq.com) about a possible corruption in one of the packages, listing the same lines you quoted in your posting.

---

### Post by mike1234 on 2008-09-06
Not sure if it's the same thing, but I've gotten these types of errors when repositories are outdated or no longer available. One reason I stick with official or trusted repo's. Last thing I want to do is screw up synaptic software sources.
 
M.

---

### Post by kiwi-pete on 2008-09-07
Thanks for the help guys, i will pop over to winehq for a look see...........

---

### Post by kiwi-pete on 2008-09-28
Thanks for all the help and suggestions, I have done a fresh install of Ubuntu and am in the middle of re-installing everything, being careful about what i put back. :)

---

