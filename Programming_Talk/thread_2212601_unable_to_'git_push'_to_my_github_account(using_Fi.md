---
title: "unable to 'git push' to my github account(using First time)"
date: 2014-03-22
forum: Programming Talk
---

### Post by IAMTubby on 2014-03-22
Hello,
 I signed up for a Micro account today at github and created a repository called Hello-World. These were the steps given to me at github upon clcking the Create Repository button,
```
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/IAMTubbby/Hello-World.git
git push -u origin master
```


However, on running the 'git push' command, I get an error as follows
```
$ git push -u origin master
Username: 
Password: 
error: The requested URL returned error: 403 while accessing http://github.com/IAMTubby/Hello-World.git/info/refs


fatal: HTTP request failed
```

How do I perform a 'git push' from my account ?

When I repeated the process the next time, I was errored out at the 'git remote add origin' step itself.
```
$ git remote add origin https://github.com/IAMTubbby/Hello-World.git
fatal: remote origin already exists.
```

Please advise.
Thanks.

---

### Post by IAMTubby on 2014-03-22
I tried with one more UserAccount and Repository and it worked. Which means nothing's wrong with my git versions/environment etc.

I have ensured that in the **_one in which it's not working**_
 1. It is a public repository
 2. The username and password when I do a 'git push' are correct.
 Where  else could it have gone wrong ?

I have one more question - For my github account which works, at the time of account creation, it was said that the free scheme gives you 0 public repositories. Then how am I able to git push from this account which is free ?

Thanks.

PS : It's the time first time I'm using git. If this is the not the right place to post these queries, please move it to another sub-forum or notify me. I shall take down the post.

---

### Post by trent.josephsen on 2014-03-22
The command you posted isn't consistent with the error message:
```
git remote add origin **https**://github.com/IAMTu**bbb**y/Hello-World.git
```
```
error: The requested URL returned error: 403 while accessing **http**://github.com/IAMTu**bb**y/Hello-World.git/info/refs
```
Please copy and paste, don't type, commands and error messages.

Run `git remote -v` to verify the origin URL.

---

### Post by IAMTubby on 2014-03-23
> **trent.josephsen said:**
> The command you posted isn't consistent with the error message:
trent.josephsen, that was extremely irresponsible on my part. I promise not to repeat this in future.

I have retried the steps and it works fine, I'm able to see my files on github.

I just have a general question though regarding github,
 At the time of my github account creation, it was said that the free account would give me 0 repositories. Then how am I able to post my files and see it available online ?

Thanks.

---

### Post by drmrgd on 2014-03-23
I thought the major difference between the free account and the paid account was the ability to have private repositories.  IIRC, only the paid account allow for private repos, while the free accounts require that the repos are public.  I have a free account myself, and I've not come across any limitations on the number of repos that I can have.  In fact, I just did a quick check and I think this is accurate:

[https://github.com/pricing](https://github.com/pricing)

---

### Post by IAMTubby on 2014-03-23
> **drmrgd said:**
> I thought the major difference between the free account and the paid account was the ability to have private repositories.
Thanks drmrgd, trent.josephsen.
Marking the thread as solved.

---

