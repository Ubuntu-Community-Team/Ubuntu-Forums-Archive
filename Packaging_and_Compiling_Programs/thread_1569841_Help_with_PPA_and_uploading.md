---
title: "Help with PPA and uploading"
date: 2010-09-07
forum: Packaging and Compiling Programs
---

### Post by KdotJ on 2010-09-07
Hey people, I have a project on launchpad and I also have a registered PPA which I created a day a go. Now am I correct in thinking that projects and bzr branches etc are independent of packages and PPA's? And that to have a PPA of a package you don't need a corresponding project or branch?

So I made my program and packaged it following the guidelines found [here]("https://wiki.ubuntu.com/PackagingGuide/Basic#Building%20the%20Source%20Package") and [here]("https://help.launchpad.net/Packaging/PPA/BuildingASourcePackage"), and then uploaded it using the guidelines outlined  [here]("https://help.launchpad.net/Packaging/PPA/Uploading").
The package uploaded with no errors to launchpad, however nothing shows up on there. Even after giving it 24 hours just in case processing was slow... but still nothing. Also, when I try to add the PPA to my repos on my machine, it throws the error:

```
Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~kdotj/+archive/ppa
```

So does this mean that launchpad haven't created a key for my PPA yet? Or just that I can't add it as there is nothing in it?

I am building my own package from scratch and not re-packaging an existing Ubuntu package, the version number is at 1.0-0ubuntu1.

What could be the reason that nothing is my my PPA?

Thanks

---

### Post by KdotJ on 2010-09-08
Sorted it, please delete thread if needed

---

### Post by inameiname on 2010-09-19
How did you sort this? I'm finding the same issue, where my packages that seem to be successfully uploading isn't being found in my PPA. However, I am able to add my PPA, so that's not an issue.

---

### Post by KdotJ on 2010-09-19
Well mine was to do with having "maverick" in the changelog, and my launchpad needing it to be "lucid". This solved the issue for me, not that I really know the details lol, I was just lucky with this

---

### Post by inameiname on 2010-09-19
I see. Guess that isn't my issue since I am using lucid, and put lucid in my changelog. Ah well. Thanks for the reply, though.

---

