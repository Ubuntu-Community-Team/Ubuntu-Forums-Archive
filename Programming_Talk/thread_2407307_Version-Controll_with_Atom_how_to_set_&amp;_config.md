---
title: "Version-Controll with Atom: how to set &amp; configure the interaction of Atom and Github"
date: 2018-12-02
forum: Programming Talk
---

### Post by dilbert_one on 2018-12-02
hello dear ubuntu-experts, 

**the question i am working on:  **Version-Controll with Atom: how to set & configure the interaction of Atom and Github

i am pretty new to Atom and github - so i have a question: how to get up and configured the ATOM-editor so that it works with the Github-Account 

regarding the atom-manual on the following page i have several questions: 
[https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/](https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/)

i think that for a beginner in ATOM - it is the question how to connect to the Github-Account. The below mentioned Atom-Manual notes how to work with the Git Account.  But the question of the day is : how to get to the 

#interaction of Atom with the Github-account!?
that is the first question. 

 

cf: [https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/](https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/)

> ### Version Control in Atom
> 
> Version control is an important aspect of any project and Atom comes with basic [Git]([https://git-scm.com](https://git-scm.com)) and [GitHub]([https://github.com](https://github.com)) integration built in.
> 
> In order to use version control in Atom, the project root needs to contain the Git repository.
> 
> #### Checkout HEAD revision
> 
> The <kbd>Alt+Ctrl+Z</kbd> keybinding checks out the `HEAD` revision of the file in the editor.
> 
> This is a quick way to discard any saved and staged changes you've made and restore the file to the version in the `HEAD` commit. This is essentially the same as running `git checkout HEAD -- <path>` and `git reset HEAD -- <path>` from the command line for that path.


cf: [https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/](https://flight-manual.atom.io/using-atom/sections/version-control-in-atom/)

how to start to configure the ATOM in order to get interaction with my GitHub-Account? 

love to hear from you

---

### Post by spjackson on 2018-12-02
OK... besides this thread, there are 3 more where you appear to be asking the same question:
[https://ubuntuforums.org/showthread.php?t=2407303](https://ubuntuforums.org/showthread.php?t=2407303)
[https://ubuntuforums.org/showthread.php?t=2407142](https://ubuntuforums.org/showthread.php?t=2407142)
[https://ubuntuforums.org/showthread.php?t=2407128](https://ubuntuforums.org/showthread.php?t=2407128)

However, I'm afraid that I am not all that clear about what you are asking.

I tried Atom for a while but couldn't find a compelling reason to use it. Nor am I motivated to use git or any version control from within an editor or IDE - I use git from the command line & occasionally via 'git gui'. However...

If you already have a local clone of a github repository, then when you open the project in Atom, this will be recognised. If you don't have a local clone, then you can clone it from within Atom: "Ctrl-Shift-P" and "Github: Clone" - see [https://flight-manual.atom.io/using-atom/sections/github-package/#clone-repositories](https://flight-manual.atom.io/using-atom/sections/github-package/#clone-repositories)

If this isn't what you are asking, then please try to explain more clearly what you want to know... although an Atom forum might be more helpful. I don't recall seeing any Atom threads on Ubuntuforums apart from yours.

---

