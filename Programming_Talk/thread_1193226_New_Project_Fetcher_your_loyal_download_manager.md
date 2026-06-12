---
title: "New Project: Fetcher your loyal download manager"
date: 2009-06-21
forum: Programming Talk
---

### Post by blacksadness on 2009-06-21
Hey,
First of all sorry if this is the wrong section, please redirect me to the correct section in that case as i've obviously missed it.
I'm thinking of writing a new download manager as i'm no longer satisfied with d4x (i use it though i think we can do better).
i have set some ideas, of basic features i plan to have, and any idea, guides to start are ofcourse welcome
i have also started a launchpad project [https://launchpad.net/fetcher](https://launchpad.net/fetcher)

Ok, here are my ideas:
Functionality:
    Use libcurl for downloading (also lookup other libraries)
    be able to use multiple parts and servers.
    Detect idle time and be able to download only at that time if needed
    Scheduling features
    Have the ability to detect files with no resume functionality to exclude from idle time downloading and scheduling.
                
Diving in:
    Assuming libcurl has the interfaces to start a download, stop it, resume it and restart it we need to find the right ways to initialize each of these functions in our classes.
Possible Usecase :
  User adds a download link, provides the number of chunks he ultimately wants, a download speed perhaps, authentication, proxy settings, and a hole lot of things i probably forgot.
  The app connects to the download link with the info provided, gets the size, find out if the server supports resuming
    if it doesn't it returns that feedback to the user, stores it in internal values and start getting the file.
    it does, the app then divides the size to equal chunks depending on the user arguments (we'll probably have a default)
    for each chunk, the app initializes the download, at this step, the user might have specified multiple download sites, we have to check them all, and randomly but equally (maybe some complicated algorithm here) split the servers.
        every time a chunk is done, we divide one the remaining chunks in 2 to aid it.
        Scheduling and idle time detection work on these steps, to pause and download accordingly.

---

### Post by CptPicard on 2009-06-21
Great, can't wait to see you get some code started :popcorn:

---

