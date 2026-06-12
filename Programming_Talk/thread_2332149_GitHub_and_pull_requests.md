---
title: "GitHub and pull requests"
date: 2016-07-28
forum: Programming Talk
---

### Post by Drone4four on 2016-07-28
I&#8217;ve cloned the [Zeegaree repository by mivoligo]("https://github.com/mivoligo/Zeegaree") on GitHub to my local machine.  I installed the python dependencies and have the app up and running.  Zeegaree is a terrific little app. 


Another user [recently raised an issue]("https://github.com/mivoligo/Zeegaree/issues/6") with certain required deps like python-gobject + python-dbus which aren&#8217;t listed in the README.md.  So I updated the local README.md with python-gobject + python-dbus, added it to the staging area, and committed it.  Now with rsa configured properly, I invoke: 
```
$ git push origin master                 
Username for 'https://github.com': angeles4four
Password for 'https://angeles4four@github.com': 
remote: Permission to mivoligo/Zeegaree.git denied to Angeles4four.
fatal: unable to access 'https://github.com/mivoligo/Zeegaree.git/': The requested URL returned error: 403
$
``` I figure this indicates that since according to the project owner I am not an authorized contributor, I can&#8217;t make the change in the official repo.  I have two questions:

[LIST=1]
[*]Does this mean I have to fork it thus making it my own in order to make changes?
[*]Is there a way for me to submit a change for the original owner to review?  
[/LIST]
The answer to that second question is a pull request, right? I submitted a pull request but that change was made with the edit button on the project&#8217;s GitHub webpage in my browser which shows me [here]("https://github.com/mivoligo/Zeegaree/compare/master...Angeles4four:patch-1") but not [here]("https://github.com/mivoligo/Zeegaree/pulls") and I don&#8217;t know why.

So I&#8217;ve successfully submitted a pull request, but I did it in the GitHub interface in my browser.  How do I do that from my shell?

I&#8217;m about half way through a udemy course on how to use Git and GitHub and based on the course material I can&#8217;t answer these questions.

---

### Post by Rocket2DMn on 2016-07-29
I'm not sure it's possible (OOTB) to submit a pull request between two remote repositories (e.g. your forked repo on GitHub and the upstream repo on GitHub).  I think the *git request-pull* command is only between your local copy and the target repo.  A google search reveals a wrapper tool called [hub]("https://hub.github.com/") that allows you to do this.

My typical approach is:
[LIST=1]
[*]Fork the repo
[*]Checkout fork
[*]Create branch, make changes, commit to branch
[*]Push branch to the fork
[*]Use the GitHub web interface to create the PR
[/LIST]

---

### Post by Drone4four on 2016-07-29
Thank you **Rocket2DMn** for your reply.  

You said: > **Rocket2DMn said:**
> My typical approach is:
[LIST=1]
[*]Fork the repo
[*]Checkout fork
[*]Create branch, make changes, commit to branch
[*]Push branch to the fork
[*]Use the GitHub web interface to create the PR
[/LIST]

My first step in downloading and using some else's source code on GitHub is to clone a repo.  I've never forked one before.  So you're saying that rather than cloning an original, I instead I should fork it, then clone it locally, push my changes up to my remote fork and then how do I suggest my changes be merged into the repo belonging to the original owner?

---

### Post by papibe on 2016-07-29
Hi Drone4four.

Take a look at this video from GitHub itself on how to collaborate using git and github: [First Look • Collaboration with Git and GitHub]("https://www.youtube.com/watch?v=SCZF6I-Rc4I").

It starts very basic, but at about the 1:08 mark, it describes the standard practice, which  Rocket2DMn already described.

Hope it help. Let us know how it goes.
Regards.

---

### Post by Rocket2DMn on 2016-07-30
> **Drone4four said:**
> Thank you **Rocket2DMn** for your reply.  

You said: 

My first step in downloading and using some else's source code on GitHub is to clone a repo.  I've never forked one before.  So you're saying that rather than cloning an original, I instead I should fork it, then clone it locally, push my changes up to my remote fork and then how do I suggest my changes be merged into the repo belonging to the original owner?

"Clone" is what I meant by "checkout" - sorry to muddle terms (different version control systems sometimes use different terminology). But yes, if you're going to make changes to the original source code, you fork the repository to your own GitHub account.  What this really is is just a clone of their repository on GitHub's servers, then when you clone to your local machine, you have a clone of the clone (i.e. a clone of your fork of their original GitHub repository).

After you push the changes you make in your local clone to your fork on GitHub, you can use the web interface to open a pull request (PR) to merge your changes (now on your GitHub fork) into the original author's GitHub repository.  Alternatively, see the third-party software I mentioned above if you want to create the PR from the command line on your computer (though the web interface is much easier IMHO).  Learning command line tools is great, but graphical and web interfaces exist for a reason - because they are typically more intuitive and less error-prone :).

---

### Post by Drone4four on 2016-07-30
Thank-you **papibe** for that helpful YouTube video.  The content beginning at around 1:08 and which continues to the end of the video clearly demonstrates how to perform a pull request. The GitHub UI in that video is slightly out dated, but still enormously helpful.  And thanks **Rocket2DMn**, I will be sure to use the GitHub UI to make pull requests.

---

