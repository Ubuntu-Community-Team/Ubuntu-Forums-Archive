---
title: "Fixed and compiled a prog, now Synaptic wants to 'upgrade' it to the unfixed version"
date: 2006-04-19
forum: Programming Talk
---

### Post by jazzmuzik on 2006-04-19
In Breezy there was a bug in Noteedit. I mentioned it another forum. Anyway, I fixed it in source code, recompiled the package to a deb file and reinstalled it. All is well with Noteedit. But now Synaptic wants to upgrade noteedit to the one it thinks I should have even though they are the same version number. It's like the unrepaired version is competing with the fixed version. I've "locked" noteedit in Synaptic, but that doesn't matter. When I boot up the "Software Updates" program keeps reminding me of this available update. Is there a way to avoid this? Should I have incremented the notedit version number or something in the deb package?

---

### Post by nocturn on 2006-04-20
[QUOTE=jazzmuzik]In Breezy there was a bug in Noteedit. I mentioned it another forum. Anyway, I fixed it in source code, recompiled the package to a deb file and reinstalled it. All is well with Noteedit. But now Synaptic wants to upgrade noteedit to the one it thinks I should have even though they are the same version number. It's like the unrepaired version is competing with the fixed version. I've "locked" noteedit in Synaptic, but that doesn't matter. When I boot up the "Software Updates" program keeps reminding me of this available update. Is there a way to avoid this? Should I have incremented the notedit version number or something in the deb package?[/QUOTE]

You can use the menu in synaptic to lock a package to a specific version, I did this to have an older wine version.

---

### Post by Kimm on 2006-04-21
He said he locked it.
You can make the version number in your pacakge higher then the repository version number, thus fooling the package manager. Or, if you are sure that Ubuntu wants to "upgrade" it to the same version installed, make sure that the version number in your package is **exactly** the same as the original package.

I.e:
your version number might look like this: 1.0-1
and the ubuntu version number looks like this: 1.0ubuntu1

So synaptic might get confused.

---

### Post by jazzmuzik on 2006-04-21
Hmm. The version numbers are a bit different. THis is what synaptic properties shows for the Noteedit package:

2.7.1-2ubuntu1 (breezy)

vs. my compiled version:

2.7.1-2ubuntu1 (new)

It's the "(new)" text that is different.

I guess I'll try incrementing the version number next time I repair/compile Noteedit.

---

