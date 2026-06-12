---
title: "Disable keyboard buttons with Javascript"
date: 2008-10-26
forum: Programming Talk
---

### Post by dyous87 on 2008-10-26
Hello everyone,

I have a questions that maybe someone on these forums would be able to help me with.

I am writing a simple application for a client of mine that needs to launch on startup when a user logs into there workstations. The purpose of this application is to gather some information and then publish it to a database before giving the user the ability to use the computer.

The application is for Windows XP workstations and needs to be unavoidable in that the user cannot use the computer at all before completing the request. 

The way I have done it so far is by creating an .hta application (an html application that can be run locally as an executable in Windows). I have the .hta launching in full screen without any maximize or minimize buttons. 

What I need to know now is if there is anyway in Javascript to be able to disable certain buttons on the keyboard that would give the user the ability to exit or minimize this application. Examples are: the alt-f4 combo or the windows key. If I could somehow add some type of Javascript code to my html that would disable these buttons it would allow me to make the application unavoidable.

I hope I made this clear and I thank you very much in advance for your help.
David :)

---

### Post by Tony Flury on 2008-10-27
to the best of my knowledge, nothing in javascript can disable the keyboard, or even detect keys being pressed (unless of course the user has an input box in foucs where they are meant to type).

I would strongly suggest that using javascript for this is the wrong technology - think of what javascript is designed for (interactivity on web pages).

To actually do this you probably actually want to intercept the windows login sequence (is it winlogin - not sure) and provide your own version that does what you want - this is non-trivial.

---

### Post by jespdj on 2008-10-27
This is most likely not possible with JavaScript on a HTML page, because it would mean there's a huge security problem.

Suppose that JavaScript from any arbitrary website could mess with the keyboard like that, and for example prevent you from closing the browser window. That would give people who want to write malicious scripts a great tool to annoy users.

I agree with Tony Flury, JavaScript is not the technology you'd want to use to solve this problem.

I think that even with other programming languages / environments it will be difficult to achieve what you want. The user could for example press Ctrl + Alt + Delete to bring up the task manager and kill your application. As far as I know, it's (almost?) impossible to intercept Ctrl + Alt + Delete on Windows.

---

### Post by tom66 on 2008-10-27
You could have a parent application running in the background. When the *.hta is killed, the parent application launches it again.

Alternatively, you could create your own winlogon; you must supply a few features, such as the Secure Attention Sequence dialog, but you'll probably be able to find something on Microsoft's website about this.

---

### Post by dyous87 on 2008-10-27
Thanks for all of your help I really appreciate it. Using some reference from MSDN and google I have came up with some code that actually accomplishes most of what I want done:

```
function CheckKeys()
 {
    function cancel()
     {
     // local function
        event.keyCode = 0;
        event.cancelBubble = true;
        return false;
     }
    var allowedBack = "input,textarea,";
    with(event)
     {
        if(altKey&&keyCode==115) // disable alt+f4
         {
            return cancel();
         }
    if(keyCode==116) // disabe f5 key
     {
        return cancel();
     }
    if(altKey&&keyCode==9) // disable alt+tab
         {
            return cancel();
         }    
    if(keyCode==91) // disabe Windows key
     {
        return cancel();
     }
     }    
 }
```This works in disabling alt-f4 and f5 but it does't seem to work for disabling alt-tab or the Windows Key. I'm looking now if there is anyway I can even get this done. Do any of you have any idea?

Thank you,
David

---

### Post by jespdj on 2008-10-28
So you're going to try to do this with JavaScript anyway?

What if the user presses Ctrl + Alt + Delete to bring up the task manager to kill your application?

---

### Post by dyous87 on 2008-10-28
> **jespdj said:**
> So you're going to try to do this with JavaScript anyway?

What if the user presses Ctrl + Alt + Delete to bring up the task manager to kill your application?

Well since all of the users are non privileged on these workstations, the task manager has already been disabled by the administrator in the policy so that wouldn't be an issue. Basically all I need to try to get done now is try to disable alt-tab and the windows key however I have alreayd been told that it will not be a major issue if I can't since none of the users will likely be savy enough to avoid the survey.

---

