---
title: "where to find up to date information for 16.04"
date: 2016-04-26
forum: Recurring Discussions
---

### Post by henrykyonza.1 on 2016-04-26
I'm looking at a lot documentation lately trying to figure out a problem I have, but I'm running into an even bigger problem..

Most of the instructions and directions I find are years out of date. Most of the applications have changed or been abandoned.the command lines functions are not exactly the same. Every library and dependency is different. A lot of apps have been removed or droped from the repository and what can be found is not built for the latest ubuntu.And there is no central respiratory for information for changes unless you are willing to go to the source code and read the entire history..

With the newest lts 16.04 i have found very little updated documentation..

And it's getting massively frustrating at the mess that one had to wade through to find relevant info.

Then add that I don't have the internet at every location that I have a computer and there seems to be no basic or advanced user manual in downloadable form...And every help button in any app is a web link because everyone thinks text help file are to large to include with the app.

What is a user to do?
Give up and go back to a monolithic nightmare that at least has documented it's every stupid change for the worse?

(And yes I posted a help here but my question is obviously not an easy answer which I knew before I posted it)

So really the question is

Where can I find answers that are 100% guaranteed to be relevant and work with ubuntu 16.04 not every release before?

---

### Post by kc1di on 2016-04-26
Hello henrykyonza.1  and welcome to Ubuntu.
16.04 is fairly new and there won't be a lot written about it yet but it will follow soon.  
in the meantime you can start with the installation guide found [here.]("https://help.ubuntu.com/16.04/installation-guide/")

If you can find a copy of Ubuntu Unleashed it will contain a wealth of information much of which will remain relevant for many release cycles. 
the terminal command remain very constant. 

You will get better results if you as specific questions rather than be rate the lack of general information.
If your having a specific problem with a specific task or procedure ask the question in the appropriate forum and provide as much info as possible. 
These pages may be of help to you also:
[https://community.ubuntu.com/help-information/finding-help/support/]("https://community.ubuntu.com/help-information/finding-help/support/")
[http://community.ubuntu.com/contribute/support/ubuntu-forums/]("http://community.ubuntu.com/contribute/support/ubuntu-forums/")

---

### Post by bapoumba on 2016-04-27
*Thread moved to **Recurring Discussions**.*

---

### Post by yoshii on 2016-06-13
I very much agree with you Henrykonza.  It's sad how much Ubuntu and Linux info is out of date.  
I guess there just aren't enough knowledgable volunteers to keep everything going.  

 I have had similar issues and I also don't have internet access at home, for example.  
However, I was able to do some successful offline downloads using this technique:  [https://www.youtube.com/watch?v=CaJWrKyLUw0](https://www.youtube.com/watch?v=CaJWrKyLUw0)
Also helpful was this command:

sudo apt-get install --install-recommends --install-suggests --download-only gdebi

That command attempts to download gdebi package manager without actually installing it.  
It also usually downloads the needed dependencies as well as those that might also be needed.  

The results are found in /var/cache/apt/archives/ and can be copied from there to a flash drive.  
Then, you can copy the files from the flash drive to a new empty folder inside your Home area of your hard drive.  
Inside that new empty folder, you can run "sudo dpkg -i *.deb" which will attempt to install all of the debian archives found inside that folder.  

Doing that in conjunction with the video command, I was able to install a lot more stuff.  

I hope this helps you out.

---

### Post by ian-weisser on 2016-06-13
> **henrykyonza.1 said:**
> I'm looking at a lot documentation lately trying to figure out a problem I have, but I'm running into an even bigger problem..

Most of the instructions and directions I find are years out of date. 

[...]

Where can I find answers that are 100% guaranteed to be relevant and work with ubuntu 16.04 not every release before?

> **yoshii said:**
> I very much agree with you Henrykonza.  It's sad how much Ubuntu and Linux info is out of date.  
I guess there just aren't enough knowledgable volunteers to keep everything going.  

[...]

Maintaining the documentation is a community responsibulity. All volunteer.
There are plenty of knowledgable volunteers, but few are currently willing to volunteer to help the Documentation Team.

Several reasons for that.

Maintaining useful, readable documentation is not easy. It's a skill. An expensive skill - good documentation writers can command big salaries.
We're asking inexperienced volunteers to learn that skill and do it for free...without training, coaching, or feedback...and then some complain that they are not doing it to a professional standard.

Writing documentation can also be terribly frustrating. Everyone's a critic; everyone's an editor. I have written clear, concise pages...only to have others come along and obfuscate and re-edit my paragraphs into a confusing mess.

The technical skills needed to identify and solve a problem are not the same communication skills needed to clearly transmit the solution to others. Many developers love coding and hate wiriting about it.

If you feel very strongly that Ubuntu should have better documentation, do feel free to join the Ubuntu Documentation Team and spend a few days taking a swing at the problem.
The problem surely won't go away on it's own.

---

