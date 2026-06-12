---
title: "Why proper error handling should ALWAYS be done"
date: 2007-11-16
forum: Recurring Discussions
---

### Post by j_g on 2007-11-16
Let's start off with an anecdote. I once used some shared lib that employed a call to longjmp() to handle error conditions. As usual with a technique like that, I found that the lib was leaking memory and resources. So I had a conversation with the original author that went like this:

==========================

ME: Why did you use longjmp() to handle errors?

HIM: I considered it to be the best design decision under the circumstances.

ME: I'm not sure what circumstances you mean, but why not try to add some resource tracking so you can recover better when that longjmp happens?

HIM: It would have been pointless.

ME: Why??

HIM: Because my code uses some other code that also doesn't do proper error handling. It leaks memory, and also doesn't even check whether malloc returns a nul pointer. So I figured that, as long as I'm inheriting all that behavior, I may as well not worry about whether my code does the same things.

==========================

I got so mad about it that I totally rewrote his code, jettisoning the other poorly designed code he was using, ripping out longjmp altogether, and doing proper error handling. The net result is that it stopped leaking resources for me, and all the other people who used my rewrite.

Now back to the present, we have the following reply (posted off-topic in another thread):

[QUOTE=pmasiar]"note that due to overcommiting on Linux OOM errors are generally not handled by malloc() returning NULL, but by killing processes via the OOM killer. So spending much time thinking about handling malloc() returning NULL is generally a waste of it."

...they had a good laugh out of it[/QUOTE]

Yes, it's true that Linux runs the risk of abruptly terminating apps, and potentially losing very important data, under low memory conditions. (As an aside, I have personally experienced running Win32 software under low memory conditions. The OS properly allowed the app to become aware of the condition, and to continue running. I consider Windows to be more robust in this scenario).

But just because the OS may abruptly kill an app (and potentially any work the user has done with that app) is no more an acceptable explanation for not doing proper error handling, than it was in the case of that anecdote above.

Now, when an app abruptly terminates and I lose some work, I get mad. I have no doubt nearly every other enduser has the same reaction. If it's due to a bug (ie, unintentional programming error) in the software, I try to be understanding. I'm a programmer too, and we all make mistakes. (On the other hand, most endusers don't make that distinction. If a newcomer to Linux finds the software he's using to be unstable, regardless of why, he's going to say "Linux is a piece of ____, and I'm going back to Windows and spend the next couple months telling everyone I know that Linux is a piece of ____". That's how it is. If you don't know this to be true, you've not dealt with endusers).

But when I lose my data, tell the author of the software about it, and he "laughs" about it, telling me he designed it that way and he doesn't think it's a problem.... well, I'm going to say it, and I don't care what some overly repressive moderator thinks... I'd like to shoot the guy. I suspect that the vast majority of endusers would harbor the _same_ inclination.

Now, the Pulse Audio authors have already dismissed (with frankly little regard) this qualm about their design. (And that's a very good reason for someone to want to dismiss Pulse Audio when it's time to consider adding a flawed design as a major component to a distro. I can say, after doing my own audit of ALSA, that ALSA does NOT have an intentional design flaw that terminates a calling app. It is a vastly more robust audio system for that reason alone). But this is more than just about Pulse Audio.

Programmers, do endusers a big favor, and at all costs, try to avoid using software that has such design flaws. And resist the urge to blame your own design flaws upon someone else. Take responsibity for your own coding. Endusers don't want to hear someone pass the buck, nor care about the reasons why their app just went up in smoke, along with their work. They're going to get mad. If you just "laugh" about it, that makes matters even worse.

P.S. I'll point out that, Linux does not always handle OOM conditions by terminating an app. Well, it does under Pulse Audio. Why? Simply because Pulse Audio calls exit() regardless to handle OOM. I assume we're supposed to laugh about that. Ha. Ha. Joke's on us!

---

### Post by CptPicard on 2007-11-16
As far as I understood it, on Linux, malloc *itself* tends to kill the process and does not return NULL, right?

---

### Post by pmasiar on 2007-11-16
I just copy-pasted comments by pulseaudio developers on [http://pulseaudio.org/ticket/158](http://pulseaudio.org/ticket/158) so please don't pretend I said it and quote properly, if you are so touchy about what you said. See [here](http://ubuntuforums.org/showpost.php?p=3783739&postcount=37)
And please don't shoot developers - they are people, too :-)

---

### Post by j_g on 2007-11-16
> **CptPicard said:**
> As far as I understood it, on Linux, malloc *itself* tends to kill the process and does not return NULL, right?

Unfortunately, yes. This is considered to be a _very, very bad thing_. So as much as possible, it is to be avoided. A robust operating system seeks to avoid this in every possible way.

NOTE: Linux does _NOT_ always fail to inform the app if it can't fullfill the allocation request. In fact, it tries hard _NOT_ to do this. (Whether it does this better or worse than other operating systems can only be discovered through rigorous testing). So do not assume that you should NOT check for a 0 return, and that you _CANNOT_ recover from a failure to allocate memory. You should always assume that you'll get a 0 back from malloc (if it can't allocate your memory), and that your app will NOT be terminated by the operating system, and you can go on to deal with the situation... Well, unless you use Pulse Audio. Then your app terminates because that's how Pulse Audio was designed, and the author made a concious decision to do it this way, and believes it's the right decision. Why? He frankly admits it. He thinks "audio isn't important". Other things are more important, so your audio using app should just vanish in a puff of smoke to free up memory for other apps. (Of course, the enduser doesn't want to be informed that he's low on memory, so that he can manually close down other apps himself, saving his work. No, let Pulse Audio make that decision for you. You don't need THAT app, and THAT data, right?)

So any app that uses audio, whether it be an app where audio is even incidental (ie, maybe it's a word processor that decides to make a beep noise when you enter an invalid value -- out of memory? -- oops. You're history, buddy). I'd advise anyone using Pulse Audio to turn off any audio features of all software that may be important to you.

Let's all have a good laugh about it.

---

### Post by slavik on 2007-11-16
After reading the developer reply (thank you pmasiar for forming this bridge between us and the developers of PulseAudio) I understand the reason for a wrapper around malloc that kills the program.

Since I tend to be pragmatic (and I like to gloat about my new system) ... I have 8GB of RAM and if malloc returns NULL, I have a bigger problem on my hands ;) (before upgrade, I had 1GB of RAM and 3GB of swap, now it's just 8GB of RAM).

If a program MUST have some memory to run but can't get it, why have the program commit sepuku? Have someone else do it painlessly to the program. :)

[quote=j_g]Unfortunately, yes. This is considered to be a very, very bad thing. So as much as possible, it is to be avoided. A robust operating system seeks to avoid this in every possible way.[/quote]

My question becomes, should malloc be a blocking system call?

If I need 100MB of memory and can't do my function if it isn't there, what should I/OS do if there isn't 100MB free that I can use?

---

### Post by CptPicard on 2007-11-16
Seconded... failing memory allocations usually happen, say, somewhere deep in data structures. If you fail, those structures are usually left in an unusable state, and pushing up something like an OOM exception for explicit upper-level handling would be ugly.

From the OS perspective, running out of resources neccessitates killing off *something* so it might just as well kill the process that failed the allocation.

---

### Post by pmasiar on 2007-11-16
> **j_g said:**
> Unfortunately, yes. This is considered to be a _very, very bad thing_. So as much as possible, it is to be avoided. A robust operating system seeks to avoid this in every possible way.

In wikipedia, they would add [citation requested] tag :-) Here, we can ask: Considered by whom? In what circumstances? 

Personally I don't care about audio at all, so if audio went dead to make sure something more important could run, I am fine with that and don't even want to be bothered. I assume I can restart it later, no?

---

### Post by CptPicard on 2007-11-16
Your audio wouldn't go dead. Your entire app would ;)

Damn, it's tough being able to appreciate both sides of the argument... :)

---

### Post by j_g on 2007-11-16
> **slavik said:**
> should malloc be a blocking system call?

Absolutely not (well, not unless there's a way to disable blocking. And even then, it should be off by default). Being able to allocate memory is probably the most basic function that an app needs to do. And this may indeed be done in a situation where some important process needs to complete. So, malloc should not block an app. If malloc can't fullfill the request, it should "immediately" return 0, and not terminate the app, and let the app decide how it wants to proceed.

Note I put "immediately" in parentheses. This is because, typically malloc is a very time-consuming call. It takes awhile for it to complete. And note that it's almost a guarantee that, on a multi-tasking OS, malloc will have some sort of "memory resource arbitration". After all, malloc somehow has to manage a list of available free memory, and you can't have two threads simultaneously monkeying with that list. That's like having two cooks making one cake, blindfolding them, and giving them both the same set of ingredients. They're probably going to mess up each other's actions. So malloc itself may indeed "serialize" access to the list. In other words, it may indeed block your app. But it should ideally do so for the shortest possible amount of time, and absolutely not indefinitely. (I'm trying to explain this in a really simple, clear way. It's very complicated).

> If I need 100MB of memory and can't do my function if it isn't there, what should I/OS do if there isn't 100MB free that I can use?

The OS (essentially, malloc) should do exactly what I describe above -- not terminate you, and instead return 0 immediately.

You should do whatever you think is the best way to recover. For example, maybe plan ahead. I'll give you an anecdote to illustrate.

I once saw this error handling function in a shared lib. The function took an error number, and it returned a nul-terminated error message (for that error number). For example, if you passed an error number of 5, it would return the nul-terminated string "Out of memory". This is so that the app could display an error message to the enduser.

Now, the guy decided that he wanted to have error messages in various languages (ie, english, spanish, republican, democrat, etc). So he put all of the english messages in one text file. Then, he put all of the corresponding spanish messages in another text file. He used the computer's locale to decide which text file to reference.

This isn't the actual code, but let's say it was something like this. (NOTE: I'm showing half-finished untested code without error-checking, just to move things along):

```
char * get_error_message(int error)
{
   FILE *fh;
   char *str;
   char buf[256];

   // Open the text file
   fh = fopen(MyTextFilename, "r");

   str = 0;

   // Go through the lines, to find the line corresponding
   // to the error number
   do
   {
      str = fgets(buf, sizeof(buf), fh);
   }  while (error-- && str);

   // Make a copy of the string
   if (str)
   {
       char *temp;

       temp = malloc(strlen(str) + 1);

      // NOTE: Here the Pulse Audio author would call
      // exit()... oh excuse me, _exit()... if temp == 0.

      strcpy(temp, str);
      str = temp;
   }

   fclose(fh);

   // Return error msg to app. NOTE: App must free()
   // it when done
   return(str);
}
```

Now there's a potential problem with regard to malloc. What if the call fails? The function returns a 0 which means the app has no error message to display. Not too useful. (In fact, it's downright funny. If the app passes a 5, and malloc fails, that means the function failed to return the message "Out of memory" because... um... it ran out of memory. I laughed. I thought it was a whole lot funnier than pmasiar thought it was when the Pulse Audio author said that it doesn't matter whether you handle malloc failing).

I thought the best solution was to allocate memory, right at the start of the program, to load the text file into an array of nul-terminated strings (with an extra nul at the end). Then I rewrote his function (again not actual code):

```
char * get_error_message(int error)
{
   char *str;

   // Get the array already in memory
   str = ArrayOfNulTermStrs;

   // Go through the lines, to find the line corresponding
   // to the error number
   while (error-- && *str)
      str += strlen(str) + 1;

   // Return error msg to app. NOTE: App must NOT free()
   // it when done, nor alter it at all. Just display it as is
   return(str);
}
```

So I planned ahead by eliminating the malloc where it was very inconvenient to have it. If I couldn't alloc the mem when the app started up, well at least the user was informed of that before he started working. He didn't get to a situation where something failed, and yet he couldn't be informed what happened.

Note that an easy way of fixing it could have been to alter the malloc'ing:

```
temp = malloc(strlen(str) + 1);
if (temp)
{
   strcpy(temp, str);
   str = temp;
}
else
   str = "Please close other running programs and retry the operation";
```

Ok, maybe he doesn't get the error message he was _supposed_ to get. And it's in english which is maybe not the right language. But it's better than nothing at all, right? If the enduser follows the advice, and it works, he should be happy. And if he's happy, then you accomplished your job. Sometimes, posting an error message like the above is perfectly fine (assuming your app isn't like some heart monitor software. You have to design your program with the usage in mind).

But please, please, please don't stick a call to exit() (or _exit()) in there when malloc fails, even if the Pulse Audio author tells you (and pmasiar agrees) it's ok because your app "isn't important", and _maybe_ the OS will terminate you anyway, and the enduser didn't need to save his work anyway. Please, please, please, folks. Just don't. Your endusers will thank you.

---

### Post by pmasiar on 2007-11-16
> **j_g said:**
> But please, please, please don't stick a call to exit() (or _exit()) in there when malloc fails, even if the Pulse Audio author tells you (and pmasiar agrees) it's ok because your app "isn't important",

I really don't have opinion on audio - I mostly don't use it. So don't look at my opinion - I don't have any.

I got involved in this discussion for sole reason that you claimed there is error on unhandled exception or something, and you refused to report it to developers. I did, now we know their opinion and reasons, from both sides, and people can make their own informed opinions whom to trust. Your opinion alone looked for me too allarmistic, and my gut feeling was kinda right: there **are** valid reasons to do it the way audio developers did - and one does not have to agree with them.

Personally I consider CptPicard's comment as closest to my feeling about the issue :-)

---

### Post by pmasiar on 2007-11-16
> **CptPicard said:**
> Your audio wouldn't go dead. Your entire app would ;)

You mean if I listen to audio in Firefox, whole Firefox will go down, including email I started writing in GMail? That would piss me off!  Is it possible to start such "dangerous plugins" in separate threads, and kill only offending thread?

---

### Post by CptPicard on 2007-11-16
> **pmasiar said:**
> You mean if I listen to audio in Firefox, whole Firefox will go down, including email I started writing in GMail? That would piss me off!  Is it possible to start such "dangerous plugins" in separate threads, and kill only offending thread?

Well, now that you're asking... *yes* this is about Firefox going down because of audio failing to allocate memory, and the audio library deciding it wants to exit() the process because of this (you actually needed to ask?). If you don't "use" audio, a proper OOM check would probably just fail silently without audio, or at most, annoy you with an error message.

We're not making exceptions for threading in this discussion yet... however, if you're running under circumstances where you're hitting a hard RAM limit, as I said, the OS will generally have to kill *something* and from its own perspective, it might just as well be *anything*, including the process with the failed malloc. Subsequent error reporting and recovery are just as likely to fail OOM in modern OSes, really -- especially considering there are other processes competing for the same resources, with the same "rights" not to lose data because of their own respective OOMs.

And at any given time, there is just so much RAM to be shared... tough choices.

---

### Post by NathanB on 2007-11-16
Ubuntu comes standard with a fun game I enjoy playing -- Firefox.  I absolutely love it when I login to a forum, browse around, get prepared to respond to a post, and -- suddenly, without warning or explaination -- some errant piece of javascript causes Firefox to completely dissappear.  Oh, words cannot express the joy in my heart when that happens.

j_g:  You have uncovered the biggest secret the Open Source Software community would like to keep a lid on.  Fact is, Linux is being pushed so hard in the press and projects are so pressured to release new code with new functionality that very little attention is paid to "peer review" and tonnes upon tonnes of "codemonkey"-style code becomes the norm.  I wish you all the luck in your attempts to change this "status quo", but I hope you realize that this trend has been snowballing for a long time.  I suspect your most effective approach would be to convince someone "high up" on the 'authority ladder' of Debian or Ubuntu to establish quality code standards.  Otherwise, in the end, Ubuntu will become nothing but a large dirty snowball that nobody wants.

---

### Post by j_g on 2007-11-17
> **NathanB said:**
> j_g:  I wish you all the luck in your attempts to change this "status quo"

I do agree that there are a number of problems with the state of Linux development, and there are lots of things I'd prefer to see done differently.

But I'm not out to change the world. If someone wants to put a poor design into a distro I'm using, I'll either look for a way to disable/remove it, or look for a distro that is more acceptable to me. If things got so bad all around the Linux landscape that it ended up being worse than Windows for me, I'd just go back to Windows. (Actually, I haven't left Windows. Right now, I use Linux and Windows equally because Linux is not yet better than Windows for me. They're both about on a par, with a slight nod to Windows, for my purposes). Brand loyalty? Not for me. If something personally offers me more, I'll drop what I'm using and move to it, with no regrets at all. I've done it numerous times before.

What I'm simply saying here is...

"I know some of you are learning programming. And you're probably looking at code such as this shared lib example that I recently came across. One day, you may decide to write a shared lib too. Don't do this specific thing right here, that I'm showing you with this one example. It's bad, for reasons I'm going to describe now. Don't do it. Just... don't. Endusers, and other programmers who use your lib, will thank you for it."

That's all I'm saying. If it ends up changing the world, great. If it ends up just making one programmer aware of a better way to do things, and I happen to use that guy's stuff, that's just as great as far as I'm concerned.

I'm too much of a pragmatist to ever bother changing the world. I don't need that. I just need programmers to stop doing things like putting exit()'s in shared libs, especially ones that are difficult for me to avoid because, for example, maybe Ubuntu devs put it into the next release as a major component, and set all of the desktop apps to use it by default. Sigh.

---

### Post by Tuna-Fish on 2007-11-17
There seems to be some misunderstandings about how killing processe when out of memory happens.

1. in linux, malloc never returns 0, unless the amount asked to allocate is ridiculuosly large (just too large to fullfill)

2. When a process asks for more memory and malloc is about to fail, that process is NOT killed. instead, the code in linux/mm/oom_kill.c is used to pick a process (or in case of fork bombs, processes) to kill.

Malloc returning 0 when OOM is a ridiculously bad idea on a shared system, because quite likely the victim of OOM is not going to be the same as the process that caused it. because of this, just coding good OOM handling in your own program is not enough to make it OOM resistant, as when you use it all up, the next malloc that would fail is about as likely to be something in X or d-Bus or gnome or stuff like that. Now, none of those projects is interested in writing good oom handling for themselves, and in many cases (D-bus) they wouldn't be able to do it without data loss if they wanted.

So, when memory hits 0 on linux, linux tries to look up something that is 
a) using a lot of memory.
b) not likely to be useful
and kill it.

It'll settle for a if it can't find b.

The code at oom_kill.c is ver well commented, from the first comment block:
```

 *  Since we won't call these routines often (on a well-configured
 *  machine) this file will double as a 'coding guide' and a signpost
 *  for newbie kernel hackers. It features several pointers to major
 *  kernel subsystems and hints as to where to find out what things do.

```

Go read it before debating more about situations that never happen. (start at the last function, it is the one called from outside when OOM) 

The thing that pisses me off most about this thread, and the one before it, is that in well designed programs OOM doesn't cause data loss, not even when using those badly designed libraries. This is not because they do malloc returning 0 properly, but because they do handling termination signals properly. When linux decides to kill a task, it gives it a warning signal, some free memory from kernel reserves and plenty of time to do what it needs to to save data.

So to handle OOM properly without losing data write a term signal handler that saves data and tries to use as little dynamic memory as possible.

---

### Post by j_g on 2007-11-17
> **Tuna-Fish said:**
> 1) In linux, malloc never returns 0, unless the amount asked to allocate is ridiculuosly large (just too large to fullfill).

2. When a process asks for more memory and malloc is about to fail, that process is NOT killed. instead, the code in linux/mm/oom_kill.c is used to pick a process (or in case of fork bombs, processes) to kill.

Malloc returning 0 when OOM is a ridiculously bad idea on a shared system

Um, yes indeed that process is killed if malloc fails... assuming the call to malloc is in pa_xalloc(). There's the rub. It shouldn't be that way. That's a BAD design. That you're admitting this same thing is littered throughout important Linux modules is not reassuring, nor actually even relevant to the point. This is the same *why should I correct _my_ code, when the other guy's code will cause the system to dump processes anyway?*. (And just in case you're thinking of going there... let me just say that an enduser doesn't like losing unsaved work in _any_ running process, even if it's not the one that is currently in the foreground).

We hopefully teach people to do proper error checking, such as checking malloc for a 0 return and trying to recover -- so that the OS doesn't have to resort to the worse case scenario, and start dropping services and apps on its own. So if your apps are meticulous about error checking, and don't do braindead things like, let's say, busy-loop around that call to malloc until it succeeds, but rather simply not do whatever operation it was planning to do, then you're safe to write an OS that is more stable under low memory conditions. Windows seems pretty good at handling low memory conditions without abruptly terminating apps, but instead, giving them every opportunity to try to recover. I've personally experienced it myself. The operating system literally tells the enduser that he's running low on memory, and _he_ should choose processes/windows/whatever to close down. Windows plans ahead for this, and that's why, if it happens, it can present that notice. Now I haven't personally run Linux under low memory conditions, and I'm not looking to even try, because I have heard that it does not gracefully handle that situation. But that is not how it should be, and programmers should strive to write their software so that it doesn't have to be that way.

> when you use it all up, the next malloc that would fail is about as likely to be something in X or d-Bus or gnome or stuff like that.

Yes, I realize that it's difficult to integrate error handling among components that were written by people who may have never even spoken to each other. Obviously, Windows is written by one entity where the teams are pretty much compelled to interoperate with each other. So they can make sure that, if nearly every byte of RAM has truly been put to use, there is still enough "squirreled away" to make sure the GUI informs the user he's running low on memory, and _he_ should choose some processes/windows/whatever to close down. The Linux kernel isn't even written with a GUI in mind. That's fully outside the scope of the kernel. So yes, I imagine that it is very difficult for the Gnome desktop, for example, to do something like tell the enduser he's running low on memory if the kernel (ie, the entity doling out memory) doesn't even know what Gnome is really for.

So, if the kernel can't be sure it can advise the enduser of this condition, I suppose it has to make a decision how to recover on its own (rather than letting the enduser choose how he wants to regain some memory -- close a window, unplug some device that may cause mem to be freed, maybe close down some process, etc).

But that's irrelevant. It's a different discussion. It has no bearing upon whether an app should not bother checking malloc for a 0 return, and attempting to recover. (What you're talking about means only that a Win32 app has a better chance of not being terminated without the enduser's consent than a Linux app has). If the app asks pa_xalloc for "a ridiculously huge amount of RAM", and malloc fails, then the app _will_ be terminated. End of story. Finito. Try it. You'll see. Why? Because there's a call to exit() there. And it shouldn't be there. It shouldn't be there in other Linux shared libs either.

That's what we've been telling people in these threads.

---

### Post by LaRoza on 2007-11-17
> **NathanB said:**
> 
j_g:  You have uncovered the biggest secret the Open Source Software community would like to keep a lid on.  Fact is, Linux is being pushed so hard in the press and projects are so pressured to release new code with new functionality that very little attention is paid to "peer review" and tonnes upon tonnes of "codemonkey"-style code becomes the norm.

I use Opera, so your experience with Firefox just makes me smugger (j/k)

How familiar with OSS development? There is only peer review in OSS, in fact, that is how it grows. Coding standards exist, look at the GNU site. And different projects have different standards. 

Code Monkeys is a great show, but I sense you are using the original meaning. I wouldn't call the oldest and most stable software the result of code monkeys.

---

### Post by NathanB on 2007-11-18
> **j_g said:**
> What I'm simply saying here is...

"I know some of you are learning programming. And you're probably looking at code such as this shared lib example that I recently came across. One day, you may decide to write a shared lib too. Don't do this specific thing right here, that I'm showing you with this one example. It's bad, for reasons I'm going to describe now. Don't do it. Just... don't. Endusers, and other programmers who use your lib, will thank you for it."

That's all I'm saying. If it ends up changing the world, great. If it ends up just making one programmer aware of a better way to do things, and I happen to use that guy's stuff, that's just as great as far as I'm concerned.

I'm too much of a pragmatist to ever bother changing the world. I don't need that. I just need programmers to stop doing things like putting exit()'s in shared libs, especially ones that are difficult for me to avoid because, for example, maybe Ubuntu devs put it into the next release as a major component, and set all of the desktop apps to use it by default. Sigh.

There have recently been a number of convincing posts in these threads which demonstrate that this "exit()'s in shared libs" thing is a non-issue -- that it is simply your mis-understanding of how OOM issues are typically handled in Linux environments.  Are you absolutely SURE that you are spreading the *correct* advice to programmers who are new to shared library coding?

---

### Post by aks44 on 2007-11-18
> **NathanB said:**
> There have recently been a number of convincing posts in these threads which demonstrate that this "exit()'s in shared libs" thing is a non-issue -- that it is simply your mis-understanding of how OOM issues are typically handled in Linux environments.

Strangely enough, I have not seen those convincing posts even though I watched these threads since the beginning.

What is clear to me though is that malloc can return NULL way before the kernel's OOM killer kicks in, which allows applications (well, the ones doing proper error handling) to take the appropriate actions.

Anyway, either case the decision to exit should not belong to the library, it is the application responsibility to handle such cases, just because the author of a library has no clue where exactly his library may be used in the end.


Damn, that's for reasons like those that I'm glad I use C++ (at least if I don't have to deal with misdesigned C libraries). No memory available? Let the exception propagate... :p

---

### Post by j_g on 2007-11-19
> **NathanB said:**
> There have recently been a number of convincing posts in these threads which demonstrate that this "exit()'s in shared libs" thing is a non-issue

Um.... where??? I don't see any convincing posts detailing why there should be exit()'s in shared libs.

All we know for sure is that malloc can indeed return a 0 on Linux (I've had it happen to me before), and if you fall into exit(), then you kill off the process. This is a nasty thing to do to an enduser (because it could result in him losing unsaved work, and is just plain annoying and unreassuring). It's also a nasty thing to do to an app programmer using your shared lib.

> that it is simply your mis-understanding of how OOM issues are typically handled in Linux environments.

OOM issues have nothing to do with calling exit() when malloc fails, or calling exit() for any reason in a shared lib used by numerous apps. (It's true that Linux does allow "over-committing memory", and because of that, an OOM killer exists. I really, really wish it weren't so. I really wish that Linux didn't over-commit, and also informed the enduser when a low memory condition was upon him. But that's another problem).

> Are you absolutely SURE that you are spreading the *correct* advice to programmers who are new to shared library coding?

Yes. Check the return of malloc for 0, and gracefully handle the situation by informing the app of this situation. Do not abort the app.

Follow the advice here [http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html?page=2) (under "Check for NULL Pointer after Memory Allocation").

---

### Post by samjh on 2007-11-19
> **NathanB said:**
> There have recently been a number of convincing posts in these threads which demonstrate that this "exit()'s in shared libs" thing is a non-issue -- that it is simply your mis-understanding of how OOM issues are typically handled in Linux environments.To my knowledge, libraries should not cause ungraceful termination of applications.

The reason why a lot of Linux libraries call exit() when OOM is imminent is not because that is best-practice.  Rather, the reason is convenience, because Linux's OOM-killer will terminate a process with the highest memory consumption and lowest importance, as determined by it.  So the rationale is "why bother"?  The problem with this reasoning is that it promotes laziness.

The OOM-killer is a last-resort defence against a system failure caused by lack of memory.  Designing a shared library that relies on the OOM-killer to handle OOM situations is like removing airbags from a car because it already has seatbelts.  In other words, while it saves development time and effort, it is unsafe and not best-practice.

As we're all tech-savvy people, mostly with programming experience, some of us are professional programmers, what do we want to encourage in open source: reliable and safe software design and programming practices, or a "close enough is good enough" and "let's not do it because we can't be stuffed" approach to software?

---

### Post by aks44 on 2007-11-19
> **samjh said:**
> what do we want to encourage in open source: reliable and safe software design and programming practices, or a "close enough is good enough" and "let's not do it because we can't be stuffed" approach to software?

Reminds me of an old article I stumbled upon several times. Unfortunately I just can't find it again, so I'll try to resume it from what I remember.


The article in question was about development methodologies of two different US universities participating to FOSS software (I'm pretty sure Berkeley is one of those two). 

One uni was all about "features are the priority" and "close enough is good enough" (as you put it). IOW, as soon as it is apparently stable, don't bother with it anymore and move on to something else. Surprisingly (to me, at least) features had priority over correctness and stability. At the time I thought this was just an heresy.

The other uni (Berkeley IIRC) had the exact opposite stance. Correctness and stability were top priorities, features came last (and there were a few other criteria inbetween).


Now, I'm not saying either POV is better than the other. Without innovation things can't get better, and without proven reliability things can only get worse, so we really need both.


My current opinion is that Linux is more about innovation, and if you need unconditional reliability the BSD's are out there waiting for you.

Don't get me wrong though, this doesn't mean that we shouldn't try to enhance both. But developing 100% reliable software is definitely a very slow process (and even BSD's are far from this), so it just can't follow the innovation's pace.
Hopefully both can learn from each other though...

My biggest rant being: why ignore existing rock-solid solutions in favour of less stable solutions, out of *misplaced laziness*(*)??


PS: if anyone knows has a link to the article I'm referring to, I'd be glad to be able to bookmark it once for all. ;) It's a quite short text but very informative.


(*) We all know that a good programmer is a lazy programmer. But we better not forget that what you do now will save you tenfold work later, and what you avoid now will strike you back later... So doing it right *now* (including planning ahead) is my own personal definition of the True, Efficient Laziness (tm). And I defy anyone to be more lazy than me... :p

---

### Post by NathanB on 2007-11-19
> **j_g said:**
> Um.... where??? I don't see any convincing posts detailing why there should be exit()'s in shared libs.

All we know for sure is that malloc can indeed return a 0 on Linux (I've had it happen to me before), and if you fall into exit(), then you kill off the process. This is a nasty thing to do to an enduser (because it could result in him losing unsaved work, and is just plain annoying and unreassuring). It's also a nasty thing to do to an app programmer using your shared lib.


Noone else wants to be nice enough to say this, so I will --  If you ever write a **real world application** which attempts to allocate enough memory to cause a 0 return value, then you should step-aside and let somebody more qualified write the program.

In **actuall practice**, this "exit()" part of these library wrappers is just a comment -- it never gets executed.  If it ever does, then your program has more serious issues to contend with {for instance... its author}.

---

### Post by Wybiral on 2007-11-19
> **NathanB said:**
> In **actuall practice**, this "exit()" part of these library wrappers is just a comment -- it never gets executed.  If it ever does, then your program has more serious issues to contend with {for instance... its author}.

That makes it sounds a little more logical, but truthfully there isn't always a way to predict:

a. How much memory the user of your library may need
b. How much memory is available on your target system

Because of this, it's just not friendly to expect that there will always be memory. One of my computers only has 256mb of ram, and the one I'm on right now only has 512... It's not hard to use all of that when you're running certain applications (especially sound or video related applications).

Why is it too much to ask for the library writers to try to take care of this? Malloc usually returns NULL in those cases, and there's no reason a library shouldn't take that into consideration and try to gracefully pass it back to the library user so that they can say "well, my application is just a game, not need to worry, just exit" or "my application is handling potentially user-important data, I better report OOM to them so they can save their work".

---

### Post by aks44 on 2007-11-19
> **NathanB said:**
> If you ever write a **real world application** which attempts to allocate enough memory to cause a 0 return value, then you should step-aside and let somebody more qualified write the program.

In **actuall practice**, this "exit()" part of these library wrappers is just a comment -- it never gets executed.  If it ever does, then your program has more serious issues to contend with {for instance... its author}.

In addition to Wybiral's post, I'll add that aggressive resource management is definitely a valid idiom (eg. on dedicated servers). FYI "scalable" is not a synonym of "conservative". A truly scalable program is able to use both hyper aggressive techniques as well as highly conservative ones, depending on its environment.

The problem is that you can hardly guess when you'll "hit the wall", so by default you'll usually use aggressive methods until they fail (if they can fail gracefully...), then you'll scale down.


Anyway...
[QUOTE=dwhitney67]I'm a software engineer. For those of you who like to write poor code, **_please_ continue to do so**. It will keep me employed until the day I retire.[/QUOTE]I could hardly agree more.

---

### Post by NathanB on 2007-11-19
> **Wybiral said:**
> That makes it sounds a little more logical, but truthfully there isn't always a way to predict:

a. How much memory the user of your library may need

This is easy to predict because you can simply decide not to support users of your library who are the type that foolishly and haphazardly **abuse** system resources.
> 
b. How much memory is available on your target system

This is also easy to predict.  Just slap a sticker on the box (or a note in the download product description) which informs the possible user what the **system requirements** are.
> 
Because of this, it's just not friendly to expect that there will always be memory. One of my computers only has 256mb of ram, and the one I'm on right now only has 512... It's not hard to use all of that when you're running certain applications (especially sound or video related applications).

Congratulations!!!  You have discovered what that "exit()" call is for!!

Every Linux distro and most applications clearly indicate what they _require_ and _recommend_ in terms of system resources *before* you attempt to use that distro/app.  As an application developer, you do not want to be in the position of providing technical support for a client who attempts to run your software on less than appropriate hardware.  Do not do it.  It is a waste of their time as well as yours.  In the case that your application is ever put into *that* undesirable situation, you want your app to "exit()" immediately so that the user will clearly understand that it is not intended to function under those conditions.

P.S. -- Suggestion to the Moderators:  If you wish to reduce the occurance of these types of threads here, simply rename this subforum as "Programming Q&A" or similar.  There exist plenty of newsgroups and language-specific forums around the 'net where these discussions can be argued to death... and they are probably a more appropriate venue.  This forum's greatest asset is the answers that newcomers receive -- the rest, IMO, is immaterial.

---

### Post by kegie on 2007-11-19
> Noone else wants to be nice enough to say this, so I will -- If you ever write a real world application which attempts to allocate enough memory to cause a 0 return value, then you should step-aside and let somebody more qualified write the program.

As someone who actually writes "real world applications" where malloc() returning 0 is a very real possibility, I just want to be nice enough to tell you this: I'm sorry, but you don't know what you are talking about, and lennart of PA doesn't either. j_g is completely right in saying that a library should not look like this.

What lennart is saying in his reply to the bug report is that since audio is of low priority, having the audio process die on a failed memory allocation is not a problem. The error he makes is thinking that the audio process is exactly that, a process that only plays audio. Since this function is exposed in the PulseAudio library however, that doesn't have to be the case. The process could be any program that uses PulseAudio. For example (not the best example, but anyway), if a program that as its main functionality keeps a respirator going, but uses PulseAudio to beep when human attention is needed, this program would crash on OOM. That would of course be unacceptable. Now, such a program would definitely not use PulseAudio, but to me it is not good library design to force applications to crash without a chance to die gracefully when it would be fully possible to let them. 

Yes, there are plenty of actual real world applications where this is an issue. Not many such applications are available for Linux. I wonder why? Unfortunately as long as the developers of core OS functionality refuse to even acknowledge that there are such applications, these applications are unlikely to ever be written for Linux.

Now, this is not an attack on Linux, and other platforms have other issues. It's not even a gigantic issue (in this case). Just don't be fooled into thinking that because these particular programmers laugh at it, that it isn't real or isn't important. It is often more convenient to pretend an issue doesn't exist than it is to fix it, especially when you don't _have_ to fix it (as is often the case in free software).

The plain truth is this: This is bad library design, and it is completely fixable. Is it worth fixing in this case? Maybe not. But it sure looks bad to a "real world programmer".

---

### Post by winch on 2007-11-19
> **Wybiral said:**
> Why is it too much to ask for the library writers to try to take care of this?

Malloc succeeds when there may be no memory left when the process later uses the memory.
The malloc/free paradigm is broken. Return values from malloc simply can not fix this problem. If the problem needs to be fixed then inside each library is not the place to do it.

If you try to fix it in the libraries then.

Each library needs it's own set of platform specific and possibly even kernel version specific code just to allocate memory. All this code needs to be maintained and bug fixed.

The above point means most people can't write libraries without cargo culting memory allocation routines.

All it takes is one process that doesn't do this to trigger the OOM killer which will potentially kill a "well behaved" process.

That's why it is too much to ask for libraries to fix the problem. It's not their place to fix it and doing so has numerous downsides. Malloc was introduced precisely to remove these problems.

---

### Post by xtacocorex on 2007-11-19
> **NathanB said:**
> P.S. -- Suggestion to the Moderators:  If you wish to reduce the occurance of these types of threads here, simply rename this subforum as "Programming Q&A" or similar.  There exist plenty of newsgroups and language-specific forums around the 'net where these discussions can be argued to death... and they are probably a more appropriate venue.  This forum's greatest asset is the answers that newcomers receive -- the rest, IMO, is immaterial.
You haven't been around this forum for a while, some of us have gotten to be good friends and (I'm assuming here) are excited for a good discussion.  This is also the most thoughtful discussion this group of people have had in a while on here, tis a shame mods have had to close threads.

Since you're suggesting this why don't you go ahead and suggest a removal of the multiple "Which programming language" threads; those are far more annoying than this, and frankly piss me off because people don't know how to read the stickies.  

I like the fact that the OP is trying to raise awareness, however brash it is.  Sometimes you have to break bridges to build new ones...

---

### Post by Wybiral on 2007-11-19
> **NathanB said:**
> This is easy to predict because you can simply decide not to support users of your library who are the type that foolishly and haphazardly **abuse** system resources.

This is also easy to predict.  Just slap a sticker on the box (or a note in the download product description) which informs the possible user what the **system requirements** are.

Congratulations!!!  You have discovered what that "exit()" call is for!!

Every Linux distro and most applications clearly indicate what they _require_ and _recommend_ in terms of system resources *before* you attempt to use that distro/app.  As an application developer, you do not want to be in the position of providing technical support for a client who attempts to run your software on less than appropriate hardware.  Do not do it.  It is a waste of their time as well as yours.  In the case that your application is ever put into *that* undesirable situation, you want your app to "exit()" immediately so that the user will clearly understand that it is not intended to function under those conditions.

P.S. -- Suggestion to the Moderators:  If you wish to reduce the occurance of these types of threads here, simply rename this subforum as "Programming Q&A" or similar.  There exist plenty of newsgroups and language-specific forums around the 'net where these discussions can be argued to death... and they are probably a more appropriate venue.  This forum's greatest asset is the answers that newcomers receive -- the rest, IMO, is immaterial.

I love how simple library / software design is for you. Your philosophy of "oh s**t, exit()" will probably lead you to writing tons of stable, scalable code. When in doubt, blame your laziness on your users... Yeah... That'll work. [/sarcasm]

P.S. -- I don't think this forum is meant to be restricted to Q&A, it's a discussion forum. But if you want to tell the mods how to do their job, I'm sure they will appreciate it.

P.P.S -- Occurrence is spelled with an "e"

---

### Post by tyoc on 2007-11-19
> For example (not the best example, but anyway), if a program that as its main functionality keeps a respirator going, but uses PulseAudio to beep when human attention is needed, this program would crash on OOM.
Indeed a very bad example, you normally would not use a device that monitor something important and run apps that can take and **use** all memory in a second in that device.

> Yes, there are plenty of actual real world applications where this is an issue. Not many such applications are available for Linux. I wonder why? Unfortunately as long as the developers of core OS functionality refuse to even acknowledge that there are such applications, these applications are unlikely to ever be written for Linux.I don't get what you say about "real world applications"... I have in front of  me a real world application... I'm using it, also you are using it right now (I don't see how  you and I can be using something that is not REAL)... I can correct you in what I think you are trying to say "real-time OS applications", there is RTOS, if you want that, you should look at the possibilities.

> Unfortunately as long as the developers of core OS functionality refuse to even acknowledge that there are such applications, these applications are unlikely to ever be written for Linux.Which type of apps, I still cant see what type of apps... if it is not RTOS apps.

> where malloc() returning 0 is a very real possibilityYou mean that your apps stress the resources to even finally  cause an OOM, and that posibility is really high that in each run you fall in an OOM?, say me please what type of applications you write and in what field are you working,  Im curious about the field of the app.

malloc returning zero is not a "possibility" is a fact, other thing is: if that fact will happen or not... and that depend on a lot of factors, from system to system, user to user and so on... that is the actual possibility, not malloc returning zero.

If you write "real world applications" where that possibility is high, thus simple, try to low the possibility to happen (one way or the other, software, hardware, users, focus the usage of the machine give it a specific task, etc... etc)... if possible, if not, nice that I don't need to write such an app.


>  a. How much memory the user of your library may need
This is easy to predict because you can simply decide not to support users of your library who are the type that foolishly and haphazardly **abuse** system resources.And how you do that?, put limits?, restrictions of how many objects you can run?, write a monitor that knows the state of usage of your lib for certain thread, process or group of them?, why malloc will need to limit me the memory that I want to get? (it is something variable, if malloc have a limit say 50% of total memory, and if there is a system with very specific task running, but 1 of them need 70% of mem, how that limitation will impact it ;).

The question is simple. "How much memory the user of your library may need", is not the business of the library, his business is be the library and only of his own resources not decide before the restrictions of usage, not all the possible applications that can use it will have the same behavior and needs, because not a single restriction work for all there is no "one ring to rule them all".


> Now, such a program would definitely not use PulseAudio, but to me it is not good library design to force applications to crash without a chance to die gracefully when it would be fully possible to let them.Don't know if in this thread or in other related (all of them look  the same to me) I have said that will be nice if some one can find an app that is a client of PulseAudio and ask them if that has been the case, I also have said that would be nice to skim in the mails or bug report list of that client of app using it, for see if some of the problems they have is loosing data because that behavior.

I also have said that from what I know from servers (Pulse Audio is a server "A sound server is basically a proxy for your sound applications"... and perhaps other things), thus in that context and without see the code, I think that exit is his choice of exit the server, the worker thread or process, whatever he choice to do, I also have said well if you use pa_malloc  intead of malloc or your wrapper in your own application, thus your problem :P, but from the little that I fond in examples of play music with PA haven't seen to this moment usage of pa_malloc in those examples, only what I can judge normal in a server/client communication that is connection and interaction.


I also will like to know the place where pa_malloc is documented like API, ahvent found it to the momment.

This is what I try: [http://www.google.com.mx/search?q=pa_malloc+site%3Ahttp%3A%2F%2Fpulseaudio.org](http://www.google.com.mx/search?q=pa_malloc+site%3Ahttp%3A%2F%2Fpulseaudio.org)



-----
Also the argument about audio for a blind people is valid, but the autohr thinking that almost all people that use a PC are not blind and can stop listening data... or stop recording (see that is the client who choose how to handle/store temporarily/final that data and how to process it finally, I hardly think that they need all the audio data in more than needed eg. 1Gb of audio data to be in memory at the same time for do an effect that will have a duration of 30 seconds...).

Being for the blind more valid, simple, knowing how OOM cast the apps with his rules, get up the priority of the audio server, isn¡t? at the end, priority also work for give more importance... I guess/suppose is the reason for be there, use it.

---

### Post by j_g on 2007-11-19
> **NathanB said:**
> If you ever write a **real world application** which attempts to allocate enough memory to cause a 0 return value, then you should step-aside and let somebody more qualified write the program.

But Linux over-commits (by default). So you don't know how much memory is enough to cause a 0 return value. All you know for sure is that a 0 return value is possible, and if you "handle" it by calling exit()... well, perhaps say goodbye to your enduser's work. I strongly suspect an enduser would not look favorably upon the "qualifications" of a programmer who does this.

> this "exit()" part of these library wrappers is just a comment -- it never gets executed.

How have you determined this to be true? We've already seen that malloc can return 0. Are you claiming that the following code doesn't call exit() if malloc returns 0?

```
ptr = malloc(SomeAmtOfBytes);
if (!ptr) exit();
```

I'm not sure I'd be confident in the qualifications of a programmer who answers "yes" to the above question.

> If it ever does, then your program has more serious issues to contend with {for instance... its author}.

What specific "issues"?... (other than the sole, unsubstantiated ad hominem that the issue is the software author -- with such ad hominem arguments being a staple in the Ubuntu Programming forum with the apparent tacit approval of at least one moderator, whereas threads containing actual detailed points to back up assertations are to be locked and discouraged).

---

### Post by pmasiar on 2007-11-19
I think reasonable compromise can be established.

We all know that doing proper thing and handle all errors properly is a lot of work, can be easily 30-50-80% of the code. So for simple non-critical app like audio in most cases: whn out of memory, audio app can just die and be done with it, so more important apps can live on. If this is documented behavior, all is kosher. If it does not suit you, please be my guest take my code and add 70% of proper error handling exactly as your app needs. It is open sourse after all.

Some people like to solve **right problems** any way they can (a.k.a "hack"), other people like to solve problems **right way** or not at all. In most cases I prefer "good enough" solution over no solution. In some cases, I seek perfection, but audio is not it.

"Perfect" should not be opponent of "good enough". 
Or, as "Zen of Python" says: "Practicality beats purity"

IMHO, YMMV, I am NOT a kernel hacker. You can continue discussion, which IMHO look very close to Ambrose Bierce's [definition](http://dd.pangyre.org/d/discussion.html):

Discussion
    n. A method of confirming others in their errors
:-)

---

### Post by tyoc on 2007-11-19
> well, perhaps say goodbye to your enduser's work. I strongly suspect an enduser would not look favorably upon the "qualifications" of a programmer who does this.

Like I said, I have not read the code of PA, but reading the introduction, it say is a server, a proxy... and watching some of the samples, I not see a pa_malloc or pa_free in those samples (yes they are lite) that mean you dont need them there (at less for lite apps).

Most probably without look at code he have choice to close the PA server, NOT the client (that is all that I can argue about why he choice to do that)... do that perhaps is not acceptable from PointOfView of a shared library, but I guess is correct taking that is a "simple" server to serve to multiple clients doing sound data (IO).

Also note that like from a socket, when you read the data you not maintain all the data (eg if you gonna receive 10Gb of a file, you don't have all the file until end for store it), it is a problem of the client only  communicate back and fort interacting with the server primarily (open, close , send, receive), secondarily but more specific to a certain client (using the tools to comunicate with the server) is how to handle data and how much process at one time. also how to store or retrieve it, is a problem of the app that is using/acting like the client, the sole purpose of a server is to serve, and the client to be client of the data. what is serving? sound data input (from a mic and related.. to little input if you ask me, I dont see how it can get for example a transference in 1 sec of a input signal that is about 300Mb) and output. I mean well if the client choice to store all the temporal data in memory and then it crash or the server close the connection because it is closed, I dont see why the server should take care of more than communicating to the client things about the content. How a client handle  that... from my POV is the problem of the client programm. In other words, why would Apache care about how FF or IE display the content, or how to serve a PHP, ASP, xxDinamicPage?? it sole porpoise is to serve, the clients are the ones that display it in parts and the dynamic is work of other components (not the server), store it in a temp file or in memory, that is not the work of the server.

The above I think it apply to the case, also I repeat haven't checked the code, and don't know from which parts that function that raise this thread is called or if that is called from the client code or not, and how is the server loop, internals etc, etc etc.

---

### Post by Tuna-Fish on 2007-11-19
> **kegie said:**
> where malloc() returning 0 is a very real possibility

If you had that much experience, and/or had the decency of spending the whole 2 minutes testing it, you'd know that in "real world applications" malloc doesn't return 0.

Behold, proof:
Code:
```

#include <stdio.h>
#include <stdlib.h>
#define SIZE 20
#define AMOUNT 1073741824 // 1024*1024*1024
int main()
{
    int i;
    int*a[SIZE];
    for (i=0;i<SIZE;i++){
        a[i] = malloc(AMOUNT);
    }
    printf("pointers:\n");
    for (i=0;i<SIZE;i++){
        printf("%x\n",a[i]);
        free(a[i]);
    }
    return 0;
}

```
Result:
```

pointers:
ff8b2010
3f8b3010
7f8b4010
bf8b5010
ff8b6010
3f8b7010
7f8b8010
bf8b9010
ff8ba010
3f8bb010
7f8bc010
bf8bd010
ff8be010
3f8bf010
7f8c0010
bf8c1010
ff8c2010
3f8c3010
7f8c4010
bf8c5010

```
My machine has 1 GB ram and 2 GB swap.

I just allocated 20GB.
Malloc returns 0 when the amout it is asked to allocate is more than the biggest chunk of contiguous address space on the machine. Not a big issue on a 64 bit machine...

If you need to be sure you don't run out of mem, use calloc. it nulls the pages when it allocates, and if i repeated the above with it, it would return 0 on the 3rd allocation. I don't because I don't want to wait the time it would take to null 2gigs of swap.

---

### Post by j_g on 2007-11-19
> **winch said:**
> Malloc succeeds when there may be no memory left when the process later uses the memory. The malloc/free paradigm is broken.

You got it.

Here's how to improve it (as I noted in a different thread that a particular moderator chose to lock, making it hard to discuss such pertinent, important programming topics here, and instead readers get to wade through yet more posts from people who simply rely upon ad hominem arguments up until they can connive a moderator to stifle discussion that some advocacy case wants stifled for the sake of... purely advocacy. I mean when someone(s) answers a detailed post about programming with little more than "you're a troll", and convinces a moderator to lock the thread, that says it all. The following discussion would have gone into THAT thread since it really should be there. But what can you do when a moderator is not making logical discussion possible?).

What Linux needs is an equivalent to Win32's VirtualAlloc so that the app can literally ask the operating system if there is _actually the ability to make particular pages available right now_, and if not, the OS can tell the app "No, there isn't, so don't read/write to/from the memory". How does the OS tell the app whether the requested page is actually available or not? Much like malloc(), VirtualAlloc returns non-zero if so, or 0 if not. In other words, there are separate functions to reserve memory, versus committing memory, ie, actually ask for some virtual memory (whether over-committed or not) to be physically made available right now. (Actually, VirtualAlloc serves both purposes. But you can think of it as having two, distinct functions). The OS should expect the app to be sensibly written and properly handle being told "no". (And the app should be sensibly written. It shouldn't do something like "Well I'm just going to loop around this call to VirtualAlloc, constantly asking you to commit").

The OS shouldn't wait until the app actually accesses memory before it does the commit. It should first give the app an opportunity to say "I really _do_ intend to access this memory now, so make sure it is backed up by either RAM or the swap file. Don't just write me out an IOU that you can't cash". Plus, by an app calling this new commit function, then the OS can assume that the app is written not to do things that made Linux resort to over-committing to begin with (ie, forking to run code that shouldn't need copies of its global resources, etc. See my other thread, which is now locked so you can't discuss these things there anymore, for more details).

Of course, especially on a multi-tasking system, there is always the possibility that some "unexpected event" _could_ happen that causes the system to have to resort to freeing up RAM (even though an app hasn't yet offered to give back RAM). But if it's a desktop system with a user sitting at it, hopefully what the OS does is inform the user that he needs to free up RAM, and he should go do that now. That's why Apple took the BSD code and made exactly that happen. Apple said "We make a desktop OS. We bill this as being particularly user friendly. We'll be damned if we handle low memory conditions by terminating software without giving the user some input in the recovery. We could otherwise be ____ing him over").

> If the problem needs to be fixed then inside each library is not the place to do it.

That's exactly where we need to start doing it (right after the malloc/free stuff gets fixed). Shared libs are where it impacts the majority of apps running on a system. If the shared libs are fixed, what Linux apps I've written are fairly good to go. (I check for 0 malloc return, and gracefully recover).

But of course, it eventually needs to be fixed in all code.

> Each library needs it's own set of platform specific and possibly even kernel version specific code just to allocate memory.

Well, since distros typically update all the software apps at the same time that they update the kernel (and have an update manager that further oversees the entire system), the transition may not be as catastrophic an event as it may seem. Hopefully a distro coordinates things as well as it can (assuming that word is allowed to get out to developers).

But yes, backward compatibility can be a bitch. But dealing with it, while also allowing new features that impact usability and security, is part of the software dev process. Sometimes, you do it in a transparent way (and I think my suggestion is really quite transparent -- old apps continue to "work" but don't yield the same usability and stability as new apps), and sometimes you do it in a less transparent way (ie, Win16 to Win32 migration).

> All it takes is one process that doesn't do this to trigger the OOM killer which will potentially kill a "well behaved" process.

Yes, but the less software that does inadequate error checking you have, the less you'll see the OOM Killer, and if the word gets out to enough programmers, the better it will be. (Not via here of course, because any attempts to get the message out here are being "locked" by a moderator, without any reason given other than "we're studying something because some advocates complained". Well, at least it's good that a moderator wouldn't resort to the _extremely unprofessional_ behavior of locking a thread from all further posts, then subsequently and admittedly unlocking the very same thread to specifically allow a certain, non-moderator to post what amounted to another ad hominem argument, and then immediately relocking the thread. I mean, that would be _totally inexcusably poor behavior_).

I write lots and lots and lots of shared libs, and mine are definitely all ready to go (insofar as checking malloc for a 0 return, and gracefully handling it are concerned). I frankly would have little problem updating my code to also account for a new function to handle committing mem. It's something that I have to do on other platforms anyway, so my code already accounts for it. If other programmers did the same right from the start, they'd be well along the way too. (I'm told that Gnome has been retooling code to really improve error handling issues such as this. They even have a function that attempts to check if mem can be committed, to the extent that it can be implemented outside of the kernel, and they use that).

---

### Post by Wybiral on 2007-11-19
> **Tuna-Fish said:**
> If you had that much experience, and/or had the decency of spending the whole 2 minutes testing it, you'd know that in "real world applications" malloc doesn't return 0.

Behold, proof:
Code:


I ran your _exact_ program and got:

```

pointers:
77e42008
37e41008
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0

```

Behold... Proof.

What version of Ubuntu are you using?

---

### Post by j_g on 2007-11-19
> **pmasiar said:**
> doing proper thing and handle all errors properly is a lot of work

There's an old saying "You can have it quick. Or you can have it good.".

> whn out of memory, audio app can just die and be done with it, so more important apps can live on.

If you want to write an MP3 player that does that, fine. (But I'd still prefer one that doesn't). But if you're writing a waveform editing program (ie, Audacity) or software sequencer (ie, RoseGarden), or _an audio API used by numerous apps_, or a distro that is supposed to be for media work (ie, Ubuntu Studio), then don't do it. Just... don't.

> please be my guest take my code and add 70% of proper error handling exactly as your app needs. It is open sourse after all.

Well yeah, I kind of wish that the Pulse Audio author had instead expended his time adding features/redesigns to ALSA's code base (which has already been accepted as the audio API that apps should use) rather than come up with yet another audio API. I don't have the same qualms about ALSA that I do about Pulse Audio. But that's how it goes. What I can do is get the message out. That's even easier than fixing code that eschews the previous open source standard, and maybe shouldn't have been written anyway (if one follows your above advice).

```
In some cases, I seek perfection, but audio is not it.
```

Then ALSA already exists, is the standard, and it's not perfect. There you go.

---

### Post by j_g on 2007-11-19
> **Wybiral said:**
> I ran your _exact_ program and got:
Behold... Proof.

Yep.

Wy, this may have to do with the differences between the size of your swap file and total RAM, and his. You're probably running under a more constrained system, so you really _are_ hitting the "low memory handling" of Linux whereas some of these other guys may have systems where their test cases don't trigger the behavior (so they assume it doesn't exist). I haven't looked at the algorithm Linux uses for figuring out how much it will over-commit. It may be that this is relative to how much swap space and RAM you have. I have not heard of a way of asking Linux what this amount would be. And even if you could, it still doesn't change the fact that malloc can return 0. (Can we please put this rumor to bed?)

I think it would be more interesting if these people turned their swap space off (ie, swapoff). They may be surprised at the difference. But then, this underscores how perilous it is to not only assume what constitutes "asking for more memory than you should", but also that malloc will never return a 0.

Wait a minute. Wy, you don't live in the twilight zone, do you? Because people are telling me that what you observed can't happen.

---

### Post by Tuna-Fish on 2007-11-19
> **Wybiral said:**
> I ran your _exact_ program and got:

```

pointers:
77e42008
37e41008
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0

```

Behold... Proof.

What version of Ubuntu are you using?

64bit.

As said, malloc returns 0 if and only if there is not enough adress space available on the system. 32bit system has 2gb of address space available for user.

---

### Post by Tuna-Fish on 2007-11-19
> **j_g said:**
> Yep.

But Wy, this likely has to do with the differences between the size of your swap file, and total RAM. You're probably running under a more constrained system, so you really _are_ hitting the "low memory handling" of Linux whereas some of these other guys may have systems where their test cases don't trigger the behavior (so they assume it doesn't exist). I haven't looked at the algorithm Linux uses for figuring out how much it will over-commit. It may be that this is relative to how much swap space and RAM you have. I have not heard of a way of asking Linux what this amount would be. And even if you could, it still doesn't change the fact that malloc can return 0. (Can we please put this rumor to bed?)


There is no algorithm for that.
As I said in my post that had the code, it returns 0 if you ask for more than you have contiguous address space.

Linux will overcommit memory to infinity, but malloc returns 0 when (per process) address space runs out.

---

### Post by NathanB on 2007-11-19
> **Tuna-Fish said:**
> If you had that much experience, and/or had the decency of spending the whole 2 minutes testing it, you'd know that in "real world applications" malloc doesn't return 0.

Behold, proof:
Code:
```

#include <stdio.h>
#include <stdlib.h>
#define SIZE 20
#define AMOUNT 1073741824 // 1024*1024*1024
int main()
{
    int i;
    int*a[SIZE];
    for (i=0;i<SIZE;i++){
        a[i] = malloc(AMOUNT);
    }
    printf("pointers:\n");
    for (i=0;i<SIZE;i++){
        printf("%x\n",a[i]);
        free(a[i]);
    }
    return 0;
}

```
Result:
```

pointers:
ff8b2010
3f8b3010
7f8b4010
bf8b5010
ff8b6010
3f8b7010
7f8b8010
bf8b9010
ff8ba010
3f8bb010
7f8bc010
bf8bd010
ff8be010
3f8bf010
7f8c0010
bf8c1010
ff8c2010
3f8c3010
7f8c4010
bf8c5010

```
My machine has 1 GB ram and 2 GB swap.

I just allocated 20GB.
Malloc returns 0 when the amout it is asked to allocate is more than the biggest chunk of contiguous address space on the machine. Not a big issue on a 64 bit machine...

If you need to be sure you don't run out of mem, use calloc. it nulls the pages when it allocates, and if i repeated the above with it, it would return 0 on the 3rd allocation. I don't because I don't want to wait the time it would take to null 2gigs of swap.


Close, but you still haven't demonstrated a **real world application**.  If a **real world application** ever required direct access to more than a Gig of memory, it would not use malloc -- it would simply open a memory-mapped file.  Using a memory-mapped file, even on a 64MB RAM 32-bit machine, you can directly access up to 18 TERABYTES of storage.  This avoids the paging file (swap space), so you also get the added benefit of not causing any thread blockage do to serialization (calls that access the paging file are serialized).

---

### Post by Tuna-Fish on 2007-11-19
> **j_g said:**
> You got it.

What Linux needs is an equivalent to Win32's VirtualAlloc so that the app can literally ask the operating system if there is _actually the ability to make particular pages available right now_, and if not, the OS can tell the app "No, there isn't, so don't read/write to/from the memory". How does the OS tell the app whether the requested page is actually available or not? Much like malloc(), VirtualAlloc returns non-zero if so, or 0 if not. In other words, there are separate functions to reserve memory, versus committing memory, ie, actually ask for some virtual memory (whether over-committed or not) to be physically made available right now. (Actually, VirtualAlloc serves both purposes. But you can think of it as having two, distinct functions). The OS should expect the app to be sensibly written and properly handle being told "no". (And the app should be sensibly written. It shouldn't do something like "Well I'm just going to loop around this call to VirtualAlloc, constantly asking you to commit").

The OS shouldn't wait until the app actually accesses memory before it does the commit. It should first give the app an opportunity to say "I really _do_ intend to access this memory now, so make sure it is backed up by either RAM or the swap file. Don't just write me out an IOU that you can't cash". Plus, by an app calling this new commit function, then the OS can assume that the app is written not to do things that made Linux resort to over-committing to begin with (ie, forking to run code that shouldn't need copies of its global resources, etc. See my other thread, which is now locked so you can't discuss these things there anymore, for more details).
calloc returns a pointer to memory that has been allocated and set to 0 beforehand. Seems to do what you want. The big point here is that the os doesn't actully know how much memory it could free any given moment if it had to. Windows does this by always going the worst case, meaning most of the memory is actually wasted. When it asks the user to reduce memory use, I bet there is still several hundred megabytes free or freeable. Linux tries to soldier on until it actually really has to kill something. By the way, at this point the user will know he's low on memory, because almost no userspace code is in memory, but is executed mainly from disk. as in the system is ridiculously slow.

> 
That's exactly where we need to start doing it (right after the malloc/free stuff gets fixed). Shared libs are where it impacts the majority of apps running on a system. If the shared libs are fixed, what Linux apps I've written are fairly good to go. (I check for 0 malloc return, and gracefully recover).

unless your apps routinely ask for more memory than the address space of the architecture can handle (the actual amount of memory on the machine and how much of it is used are completely irrelevant), pointless waste of time. If you want to be sure you got the memory, use calloc.

> 
I write lots and lots and lots of shared libs, and mine are definitely all ready to go (insofar as checking malloc for a 0 return, and gracefully handling it are concerned). I frankly would have little problem updating my code to also account for a new function to handle committing mem. It's something that I have to do on other platforms anyway, so my code already accounts for it. If other programmers did the same right from the start, they'd be well along the way too. (I'm told that Gnome has been retooling code to really improve error handling issues such as this. They even have a function that attempts to check if mem can be committed, to the extent that it can be implemented outside of the kernel, and they use that).
As said before, such function exists and it's name is calloc.

---

### Post by j_g on 2007-11-19
> **Tuna-Fish said:**
> it return 0 if you ask for more than you have contiguous address space.
malloc returns 0 when (per process) address space runs out.

Wait. Are you saying that his test failed because of memory fragmentation (ie, no "contiguous" address space) or the fact that he's using a 32-bit edition of Ubuntu (and therefore is limited to about 3gig of virtual, "per process" address space)?

---

### Post by j_g on 2007-11-20
> **Tuna-Fish said:**
> calloc returns a pointer to memory that has been allocated and set to 0 beforehand. Seems to do what you want.

Nope. calloc() simply serves the purpose of initializing the memory to 0. It doesn't try to ask the OS if the pages can actually be committed, and then gracefully return a 0 (to the app) if not. It has no way to do that. (But it could if Linux had an equivalent to VirtualAlloc). All calloc() does is simply make the OOM Killer perhaps kick in sooner than it may if you just used malloc(). That could actually be even worse.

I haven't looked over that gnome function that checks if mem can be actually committed, but I have a suspicion it just may do what calloc does. And probably gnome developers figure, if Linux ever gets a function to ask the OS about page commitment, we'll substitute that, and then we'll be good to go.

> the os doesn't actually know how much memory it could free any given moment if it had to. Windows does this by always going the worst case, meaning most of the memory is actually wasted.

Oh, I wouldn't say that the memory is wasted. I want that security. In fact, I hadn't realized until recently that Linux's over-committing behavior can be effectively disabled. I'm going to investigate that, and also see if I can tune the amount of virtual address space per app, with the swap space turned off, to get it so that the OOM Killer is itself "killed". Oh, the irony.

> When it asks the user to reduce memory use, I bet there is still several hundred megabytes free or freeable.

Of virtual address (ie, swap) space? Undoubtably. Windows just will not let a swap file fill up without telling the user before it happens. And I'm sure it also keeps tabs on how much unswappable mem is committed versus how much RAM you have, and will report when things get too close for comfort.

But that can be a good thing when there's an enduser sitting there.

> Linux tries to soldier on until it actually really has to kill something.

Well, that's because it's a Unix clone, and Unix was made to be a server OS. If there's no enduser sitting at a computer, why would the computer bother to post an error message and wait for some enduser to intervene in helping to free RAM? Why would it even prepare the means to do that ahead of time? That's why Linux likes to write error messages to log files. So later on, when a human shows up well after the deed has already happened, he goes back to read about what happened. On the contrary, Windows log files exist mostly to provide MS phone/internet tech support with something to look at when the enduser calls and says "The system did *this* when I was using it".

You know, there was some guy who recently suggested that it may be a good idea to make two separate Linux kernels -- one for server use, and one for desktop use. (He apparently got totally flamed for it). It would probably be at least a good idea if Linux APIs were introduced that helped in a desktop situation (and providing an app with the means to ask if particular mem can be committed right then and there, and being told "yes" or "no" would probably be a good start).

> user will know he's low on memory, because almost no userspace code is in memory, but is executed mainly from disk.

Yeah, I read about that. It's why I want to experiment with turning my swap space off.

> If you want to be sure you got the memory, use calloc.

Can't agree with that for reasons above. That could potentially be like waving a red flag in front of a bull, as far as keeping the OOM Killer at bay is concerned.

---

