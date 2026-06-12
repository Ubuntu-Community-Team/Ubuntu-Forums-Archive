---
title: "Any opinions on the copy dialog?"
date: 2011-10-15
forum: Programming Talk
---

### Post by t1497f35 on 2011-10-15
Hi,
I'm doing a little file browser and I wonder what you think about the design the copy dialog, see the 2 screenshots, which one is better or do you think there should be a better (3d) design?

---

### Post by satsujinka on 2011-10-15
Looks just fine, but what is the behavior of multiple transfers?
Also what language are you using? If you're using C I can send you code from my own file manager project.

---

### Post by t1497f35 on 2011-10-15
Each transfer happens in its own pthread with gdk_threas_enter/leave to update the GUI. Using C++/Gtkmm. Thanks.
Did you implement the "pause" functionality? If so, I'd like to have a look at your code, since "pause functionality" is only half-way ready for now.

---

### Post by satsujinka on 2011-10-15
No i didn't do pause. In fact the way I did it the transfer dialog is an entirely different program (that I haven't actually made, thus my interest in your project, so for now the copy occurs behind the scenes.)

As for pause, if the gdk_thread implementation allows the parent thread to control the child (fork should allow for this at least.) then pause could just call sleep or something on the child thread.

---

### Post by t1497f35 on 2011-10-16
Here are the source code and a 64bit executable are in the zip file, and a screenshot of the file browser with the transfer paused.

It works well for me but the app is in alpha stage.

To run the app the user must use at least Oneiric since it requires Gtk+3.
To compile (for 32 bit) the source install libgtkmm-3.0-dev.

---

### Post by ofnuts on 2011-10-16
> **t1497f35 said:**
> Hi,
I'm doing a little file browser and I wonder what you think about the design the copy dialog, see the 2 screenshots, which one is better or do you think there should be a better (3d) design?
These application-specific progress dialogs should be a things of the past, you normally have a system wide progress/notification system...

---

### Post by t1497f35 on 2011-10-16
> **ofnuts said:**
> These application-specific progress dialogs should be a things of the past, you normally have a system wide progress/notification system...
I'm not aware of it, can you point to the API? And if it doesn't feature a pause/resume feature it's not good enough for me. Btw I noticed today that windows 8 will feature pause/resume too.

---

### Post by satsujinka on 2011-10-16
> **t1497f35 said:**
> Here are the source code and a 64bit executable are in the zip file, and a screenshot of the file browser with the transfer paused.

It works well for me but the app is in alpha stage.

To run the app the user must use at least Oneiric since it requires Gtk+3.
To compile (for 32 bit) the source install libgtkmm-3.0-dev.

Thanks! Actually, most Gtk+3 code works fine under Gtk+2. I know my file manager compiles with both. I'll take a look at it, but for now I'm working on doing a variety of common things with Haskell. Considering I still intend to use a seperate program for copying, I can still use your stuff even if I do switch to Haskell.

Anyways, just to return the favor, here's my code, an executable, and a screenshot. Since you're doing C++ I'm not too certain how helpful it will be, but considering I used iconview, it might help you if you decide to implement an iconview mode.

Also, off topic I guess, you wouldn't happen to have cross program dnd down would you?

---

### Post by t1497f35 on 2011-10-16
Thanks
as to DnD - nope, sorry, it uses its own DnD solution, that is, if you drag a file from Nautilus and drop it onto this app - it will copy/move it as expected, but there's no separate app in it that would allow another program to use its DnD functionality.
And yes, I'm gonna add a iconview/grid layout too. Since I'm not using a Gtk::Table on purpose - I'm drawing anything by hand (with Cairo) which takes effort but allows me to make it behave exactly the way I want, cause, for example, I hate the DnD in Nautilus when in List mode because underneath there's a Gtk::Table which imo is not good for such stuff.

---

### Post by satsujinka on 2011-10-16
Hmm, I'll take a look. More than likely whatever you have is better than what I do. I couldn't find any good tutorial on DnD.

---

### Post by t1497f35 on 2011-10-16
The DnD C++ tutorial:
[http://developer.gnome.org/gtkmm-tutorial/3.0/chapter-draganddrop.html.en](http://developer.gnome.org/gtkmm-tutorial/3.0/chapter-draganddrop.html.en)
the example source code:
[http://developer.gnome.org/gtkmm-tutorial/3.0/sec-dnd-example.html.en](http://developer.gnome.org/gtkmm-tutorial/3.0/sec-dnd-example.html.en)

PS: if you're willing to finish your file manager you'd rather learn Gtk3, it's worth it, it features a lot of stuff that lets you integrate better with the desktop and spares you writing a lot of code, for example, you don't have to write code that second-guesses which app should open a given file, you can also easily get the list of apps that can handle a given file type, the list goes on. I also started my file browser on top of Gtk2, but as Gtk3 is out and ships by default with Oneiric I thought it's worth it for the sheer number of welcome new features and a cleaner API.

---

### Post by satsujinka on 2011-10-17
All of my coding was done with the Gtk 3 API docs. So my file manager is gtk 3 code. It just compiles under gtk 2 as well. I only compile it as gtk 2 because I don't have a program to set gtk 3 themes. So it looks ugly if I use gtk 3. I suppose if I switched to a DE I could solve that, but I'm rather fond of dwm.

EDIT: Why is the documentation (tutorial) for the native C bindings the weakest of them all?
Anyways, I'm currently playing with Gtk2hs, the Gtk+ bindings for Haskell. They happen to have tutorials for DnD on treeview and iconview so I should be good there. I'm sort of working on writing most of my commonly used programs in Haskell so that when I change to using xmonad for a WM I can have an environment completely written in Haskell ('cause I think that would be neat.) Afterwards, if I can't get things to work out I'll go to gtkmm.

By the way, I looked at your History class and I think you should look at my List structure (the declaration is in docs.h [for that matter all typedefs, function declarations, enums, and global variables are in docs.h] and the functions are in list.h [likewise the actual bodies of the functions are in the file that corresponds with their use.]) It's fairly good at modeling history and I also use it for cut/copy/paste (I tried using it with DnD, but as I mentioned the C tutorials are horrible.)

---

### Post by ofnuts on 2011-10-17
> **t1497f35 said:**
> I'm not aware of it, can you point to the API? And if it doesn't feature a pause/resume feature it's not good enough for me. Btw I noticed today that windows 8 will feature pause/resume too.The progress bars in KDE do include a pause/resume button, so I assume the underlying architecture supports them. AFAIK this is part of an interprocess communication mechanism called 'D-Bus'. It has GTK and QT interface libraries.

---

### Post by t1497f35 on 2011-10-17
> **ofnuts said:**
> The progress bars in KDE do include a pause/resume button, so I assume the underlying architecture supports them. AFAIK this is part of an interprocess communication mechanism called 'D-Bus'. It has GTK and QT interface libraries.
Can you actually point to these Gtk/qt interfaces/APIs with pause/resume functionality as I asked before? Or are you just guessing?


@[satsujinka]("http://ubuntuforums.org/member.php?u=914974")
Yep, I also noticed that when I google around for an answer on Gtk - the answer usually involves the Python or the Mono backend.

---

### Post by ofnuts on 2011-10-17
> **t1497f35 said:**
> Can you actually point to these Gtk/qt interfaces/APIs with pause/resume functionality as I asked before? Or are you just guessing?It's not a guess, it's an induction.
The original spec:

[http://lists.freedesktop.org/archives/xdg/2008-April/009410.html](http://lists.freedesktop.org/archives/xdg/2008-April/009410.html)

I can't find an explicit doc for that (but if you ask the right question in this forum, someone may answer), but the API has ovbiously been implemented and extended:

[http://web.archiveorange.com/archive/v/bZBuSOtTBrDlFg3rT12B](http://web.archiveorange.com/archive/v/bZBuSOtTBrDlFg3rT12B)

---

### Post by t1497f35 on 2011-10-17
Thanks, but I'm sure there's no (good) Gtk front end for that, what you shown me is integration with KDE and a proposal. I know KDE is more advanced than Gnome but I'm not going to introduce a KDE/qt dependency just for that.
And since I'm pretty much done with the I/O & gui solution, I'd rather use it than write a Gnome/Gtk front-end.

---

### Post by satsujinka on 2011-10-17
Here's an idea for making pause work, though It'll be kind of brute force. I haven't looked into your code for this yet either, but I assume you use a loop that write characters from a file to another.
psuedocode:
```

boolean paused = 0;
.
.
.
for(x=getc(); x!=EOF; x=getc()){
    while(paused){}
   fprintf(dest, x);
}
.
.
.
void changePause() {
 paused = !paused;
}
.
.
.
signalConnect (pauseButton, "buttonActivated", changePause, NULL);

```

Naturally, threads make this a bit more complicated, but this is the basic idea.

---

### Post by t1497f35 on 2011-10-17
Hehe of course I'm using the idea you just described (with pthread_mutex_t locking to avoid issues). It's hard to figure out something else besides a copy loop that checks (at different levels) if there's been a pause/resume/cancel command.

My code is in io/IO.cpp, here:

[PHP]

//R for "recursive"
void
IoCopyFilesR(const std::vector<Glib::ustring> *pvFilePaths, const Glib::ustring &targetDirPath,
    Task::Semaphore &semaphore, int &hints, off_t *lastReported, off_t *readSoFar, off_t total, GuiTask *pGuiTask) {
    if(pvFilePaths == NULL) {
        return;
    }
    const int fileCount = pvFilePaths->size();
    struct stat st;
    const size_t chunk = 8 * 1024;
    void *buffer = malloc(chunk);
    gdk_threads_enter();
    Glib::ustring sTotal = Util::parseSize(double(total));
    gdk_threads_leave();
    int result;
    
    for(int i=0; i<fileCount; i++) {
        
        while(true) {
            result = pthread_mutex_lock(&semaphore.mutex);
            if(result != 0) {
                ufbErr(result);
                return;
            }
            
            Task::Option option = semaphore.currentOption;
            result = pthread_mutex_unlock(&semaphore.mutex);
            if(result != 0) {
                ufbErr(result);
                return;
            }
            if(option == Task::PAUSE) {
                Util::sleepMs(0, 300);
            } else if(option == Task::CANCEL) {
                return;
            } else if(option == Task::CONTINUE) {
                break;
            } else {
                ufbPrint("What the heck?");
            }
        }
        
        Glib::ustring readFilePath = (*pvFilePaths)[i];
        result = lstat(readFilePath.c_str(), &st);
        
        if(result != 0) {
            perror("Can't copy file");
            continue;
        }
        gdk_threads_enter();
        Glib::ustring usFileWriteTo = Glib::build_filename(targetDirPath, Util::getFileName(readFilePath));
        gdk_threads_leave();

        if(S_ISDIR(st.st_mode)) {
            result = mkdir(usFileWriteTo.c_str(), S_IRWXU | S_IRWXG | S_IRWXO);
            if(result != 0) {
                perror("Can't create dir");
            }
            *readSoFar += st.st_size;
            IoCopyFilesR(IO::fetchFiles(readFilePath), usFileWriteTo, semaphore, hints, lastReported, readSoFar, total, pGuiTask);
            continue;
        }
        if(S_ISLNK(st.st_mode)) {
            gdk_threads_enter();
            char *path = IO::readLink(readFilePath.c_str());
            gdk_threads_leave();
            
            result = symlink(path, usFileWriteTo.c_str());
            free(path);
            if(result != 0) {
                perror("Can't create symlink");
            }
            *readSoFar += st.st_size;
            continue;
        }
        
        if(!S_ISREG(st.st_mode)) {
            ufbPrint("Not gonna handle non-regular files");
            continue;
        }
        
        int readFromFd = open(readFilePath.c_str(), O_RDONLY);
        if(readFromFd == -1) {
            perror("Can't open file for reading");
            continue;
        }
        int writeToFd = open(usFileWriteTo.c_str(), O_WRONLY | O_CREAT, S_IRWXU | S_IRWXG | S_IRWXO);
        
        if(writeToFd == -1) {
            perror("Can't open file for writing");
            continue;
        }
        
        ssize_t readFileAmount;
        ssize_t num = 0;
        int skip = 0;
        while((readFileAmount = read(readFromFd, buffer, chunk)) > 0) {
            num = 0;
            while(num < readFileAmount) {
                num += write(writeToFd, buffer, readFileAmount);
            }

            *readSoFar += readFileAmount;
            
            if( (pGuiTask != NULL) && ((*readSoFar - *lastReported) > 1024*1024*10)) {
                *lastReported = *readSoFar;
                gdk_threads_enter();
                Glib::ustring sMessage = Util::parseSize(*readSoFar) + " of " + sTotal;
                pGuiTask->showProgress(*readSoFar, &sMessage, &readFilePath, &usFileWriteTo);
                gdk_threads_leave();
            }
            
            skip++;
            if(skip % 10) {
                skip = 0;
                while(true) {
                    result = pthread_mutex_lock(&semaphore.mutex);
                    if(result != 0) {
                        ufbErr(result);
                        return;
                    }

                    Task::Option option = semaphore.currentOption;
                    result = pthread_mutex_unlock(&semaphore.mutex);
                    if(result != 0) {
                        ufbErr(result);
                        return;
                    }
                    if(option == Task::PAUSE) {
                        Util::sleepMs(0, 300);
                    } else if(option == Task::CANCEL) {
                        return;
                    } else if(option == Task::CONTINUE) {
                        break;
                    } else {
                        ufbPrint("What the heck?");
                    }
                }
            }
        }
        close(readFromFd);
        close(writeToFd);
    }
    free(buffer);
}

//main copy thread
void*
IoCopyFiles(void *pTaskObj) {
    pthread_detach(pthread_self());
    Task *pTask = (Task*)pTaskObj;
    pTask->hints = IO::COPY;
    off_t totalSize = -1, readSoFar = 0, lastReported = 0;
    IO::countTotalSizeFiles(pTask->pvFilePaths, &totalSize);
    gdk_threads_enter();
    GuiTask *pGuiTask = (totalSize > 1024*1024*20) ? new GuiTask(pTask, totalSize) : NULL;
    gdk_threads_leave();
    IoCopyFilesR(pTask->pvFilePaths, pTask->targetDirPath, pTask->semaphore, pTask->hints, &lastReported, &readSoFar, totalSize, pGuiTask);
    gdk_threads_enter();
    if(pGuiTask != NULL) {
        delete pGuiTask;
    }
    delete pTask;
    gdk_threads_leave();
    return NULL;
}
[/PHP]

---

### Post by crdlb on 2011-10-19
> **t1497f35 said:**
> 
My code is in io/IO.cpp, here:


Out of curiosity, is there a reason you are not using GIO in your file manager?

---

