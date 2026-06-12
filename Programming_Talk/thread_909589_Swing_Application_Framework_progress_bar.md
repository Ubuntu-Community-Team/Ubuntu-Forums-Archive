---
title: "Swing Application Framework progress bar?"
date: 2008-09-03
forum: Programming Talk
---

### Post by Tomosaur on 2008-09-03
Alright chaps, I'm a bit puzzled about this one as I can't seem to find an answer either through trusty old Google or any of the documentation.

Netbeans 6.1 - I am playing about with the swing application framework. When you start a new project, it creates a basic skeleton app with a single window. It also gives you a status panel with progress bar.

Now, in the auto-generated code, it sets up various behind the scenes stuff like a TaskMonitor, a basic example Action (Actions use the '@Action' tag and extend a specific class for the framework to hook into).

So my app is a basic prime number generator. The user sets a limit on the number of prime numbers he wants to generate, and the generator runs in the background (I have another problem with this but I believe it stems from some cruft I've added to the program while I try to solve the problem I'm talking about here).

What I want is to hook the pre-generated progress bar up to my generator. However, I can't figure out how to do this. All of the SAF tutorials I've come across just gloss over this point, with a nice 'See how the progress bar automatically works!'. Well I don't know where I've gone wrong, but my progress bar is:

1: Non-deterministic (In the progress bar properties I have set it to act as percentage-complete indicator, but obviously since isn't bound to the generator process, this won't work, and it reverts back to non-deterministic)

2: Not always there. It seems to come and go as it pleases (Again, I think this is an issue related to some bad code I've stuffed in while I've been trying to get this working).

Is there something obvious I'm missing? I've only seen people talking about the progress bar outside of the SAF (ie: manually updated), whereas the SAF tutorials all seem to imply that it can be done in a cleaner way (ie, tied to an Action / Task).

Any help?

---

### Post by Reiger on 2008-09-03
Progress bars in Java: [http://java.sun.com/docs/books/tutorial/uiswing/components/progress.html](http://java.sun.com/docs/books/tutorial/uiswing/components/progress.html) Maybe that'll help you figure out why it doesn't work as you expected it to work. ...

---

### Post by Tomosaur on 2008-09-03
> **Reiger said:**
> Progress bars in Java: [http://java.sun.com/docs/books/tutorial/uiswing/components/progress.html](http://java.sun.com/docs/books/tutorial/uiswing/components/progress.html) Maybe that'll help you figure out why it doesn't work as you expected it to work. ...

Yeah I've stumbled across this page while I was looking for a way to fix it.

This page, however, is like the ones I talked about in the OP - ie the progress bar is updated 'manually'. I assumed there was some way to accomplish this using the SAF, as the auto-generated progress bar is created with no task to watch (ie, it is instantiated with no task.getPercentageComplete() parameter). Obviously doing it like this isn't very 'frameworky' (for wont of a better word!).

The issue is that the TaskMonitor seems to be aware when the background task is running (the progress bar becomes active, albeit in its non-determinstic mode), but I can't find a way to feed a percentage-complete value to it. Since all of the SAF tutorials I've read just gloss over the point completely, and imply that their progress bar 'just works', I feel that I've either missed something, or somehow done something wrong (although I'm not sure how I could've messed up some auto-generated code!).

Maybe I'm just asking a little too much, but it seems like there is a way to hook the pre-existing progress bar up to different tasks without having to re-instantiate it or reconfigure it every time through manually coding everything.

---

### Post by Ruhe on 2008-09-04
Have you tried to create example desktop applications in netbeans?
I've made a little sample database app.
Here is interesting generated code, it seems that they just set progress "by hands"

[PHP]
    private class RefreshTask extends Task {
        RefreshTask(org.jdesktop.application.Application app) {
            super(app);
        }
        @SuppressWarnings("unchecked")
        @Override protected Void doInBackground() {
            try {
                setProgress(0, 0, 4);
                setMessage("Rolling back the current changes...");
                setProgress(1, 0, 4);
                entityManager.getTransaction().rollback();
                Thread.sleep(1000L); // remove for real app
                setProgress(2, 0, 4);

                setMessage("Starting a new transaction...");
                entityManager.getTransaction().begin();
                Thread.sleep(500L); // remove for real app
                setProgress(3, 0, 4);

                setMessage("Fetching new data...");
                java.util.Collection data = query.getResultList();
                for (Object entity : data) {
                    entityManager.refresh(entity);
                }
                Thread.sleep(1300L); // remove for real app
                setProgress(4, 0, 4);

                Thread.sleep(150L); // remove for real app
                list.clear();
                list.addAll(data);
            } catch(InterruptedException ignore) { }
            return null;
        }
        @Override protected void finished() {
            setMessage("Done.");
            setSaveNeeded(false);
        }
    }
[/PHP]

---

### Post by Tomosaur on 2008-09-04
Thanks for the help guys - managed to figure this out by refactoring a lot of stuff. It turns out that it is sufficient to simply use the setProgress() method in each task, and the connection with the progress bar is automatically handled by the SAF.

---

