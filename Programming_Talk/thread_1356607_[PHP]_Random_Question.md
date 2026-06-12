---
title: "[PHP] Random Question"
date: 2009-12-16
forum: Programming Talk
---

### Post by jakekimpton on 2009-12-16
Ok so i have a fair knowledge of php but this is driving me mental! 

Ok so the scenario in which i'm stuck in is below

Ok so lets say 

[LIST=1]
[*]Script 1 validates some input from the user and passes it on to Script 2
[*]Script 2 checks this data for relevance, if input is irrelevant  is passes it on to script 3
[*]Script 3 finds the input relevant and so uses it and so on...blah blah blah
[/LIST]
So the problem lies at point 2, the second script isn't going to script 3, I'm using 

[php]header('Location:script3.php?action='.$action.'');[/php]No i know that this is a valid command because i've used it in the previous scripts. But for some reason when script2 tries to move to script3 it doesn't. It just wont execute this command. I've tried commenting it out and putting something like the code below which works fine. 

[php]echo "Hello";[/php]For some reason, i cant move onto the next script, it just comes back around and like it's done its' job right! And it hasn't, it's totally skipping the header location line!

Heeelp!

Note: Is it possible i cant perform header location in script 1 and then do it again in script2
Note: I would paste the code concerning, but it's too large
Note: Ignore the Obscure way of structering, it's not for a usual scenario

---

### Post by Wardje on 2009-12-16
Sending a header on a page will only work if no other data has been sent for that page. This includes newlines and such! So what you want is to place <?php on the very first line of the page that will be sent and sending the headers before any echo's and such occur in your script.

Also, browser settings might prevent on multiple "relocations" after each other without any page, but that's something you'd have to check in your particular browser then.

---

### Post by Hellkeepa on 2009-12-16
HELLo!

Also, even if you send a "header('Location:')" request to the browser, it will not stop parsing the code below. You need to kill it manually, by using "die ()" right after the "header()" call.

That said, I think you really need to take a look at how you've structured your script. Remember that even if you validate in script1, as long as you're using header-calls to send the browser to a new page, the user can easily skip the validation.
If you explained a bit more about what you wanted to do with the script, as opposed to how you've tried to solve it, we might very well be able to provide you with a better (and secure) solution to your issue. Though, from what little you've described, it sounds like you should have been doing something like this instead:
[list=1][*]Validate input, show error/warning if not within expected parameters.
[*]Check what kind of input, and from it decide what's the relevant sub-routines.
[*]**Include** the relevant sub-routines, and perform the correct tasks.
[*]Show output.[/list]
Notice the complete lack of header-calls in that, and that everything is an atomic operation.

PS: For pasting source code of a certain length, use [Pastebin.com](http://www.pastebin.com/) and add the link here.

Happy codin'!

---

### Post by jakekimpton on 2009-12-16
Ok thats sounding good. I think the first bit about die() after header() might solve it. I know that the structure which i have mentioned sounds a messy but it's because it's for a game i have to design for a unit on my Degree (lol). Users skipping validation isnt a problem. They don't even know it happens, and if they try to skip it there are fail safes to prevent skipping which returns them to where they started. I'll boot into Ubuntu in a sec as I'm in Windows 7 atm (yuck) and give it all a go. 

Back soon! :D

Edit: Ok it seems the simple but helpful die() statement sorted it. Thanks for the help!

---

