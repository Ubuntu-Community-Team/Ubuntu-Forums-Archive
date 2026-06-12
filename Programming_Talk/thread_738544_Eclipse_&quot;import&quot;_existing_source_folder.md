---
title: "Eclipse &quot;import&quot; existing source folder?"
date: 2008-03-28
forum: Programming Talk
---

### Post by ghostoroy on 2008-03-28
[SIZE="3"][FONT="Georgia"]
Hi, 

This may be kind-of a dumb question concerning development with Eclipse generally.  

I have a folder full of source code, say foo-0.x.0 that I downloaded from someplace, e.g., as foo-0.x.0.tar.gz .  I would like to be able to use this folder as an Eclipse "source folder"--however I'm not able to "import" it directly without creating a "project" for it.  To me, the existing code folder _is_ the project--the Eclipse project with a source folder inside doesn't seem right: I prefer /workspace/foo-0.x.0/ to /workspace/foo/foo-0.x.0.  

I note that this functionality exists if you're using CVS or SVN from within Eclipse.  I'd like to do the same thing, except using random source folders on my filesystem.  

Sorry if this question seems a little broken; I've found that it's hard to search for examples of this just because of the generality of the search terms.  

Thanks for any advice!  

[/FONT][/SIZE]

---

### Post by andrewc6l on 2008-03-28
Eclipse really wants to create a project directory to hold its metadata. However, there's nothing that stops you from having a folder "within" a project but located outside of it.

File -> New Project

then

File -> New Folder, click "Advanced" and select "Link to folder in the file system".

I'd suggest you avoid linking folders that exist as subdirectories of your workspace directory. Linking something that's a subdirectory of a workspace directory will lead to a world of pain and resources being out of sync.

That is, create a project MyProject in /workspace/MyProject, but make sure foo-0.x.0 is in ~/foo or somewhere else not under /workspace.

---

### Post by ghostoroy on 2008-03-28
[FONT="Georgia"][SIZE="3"]Thanks, I think I'll take this as final that "there should be a project folder for each Eclipse project".  [/SIZE][/FONT]

---

