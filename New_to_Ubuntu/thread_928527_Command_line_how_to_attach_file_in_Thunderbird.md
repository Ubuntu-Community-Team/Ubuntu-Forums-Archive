---
title: "Command line: how to attach file in Thunderbird"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by ledibri on 2008-09-24
I want to do the following: to create a launcher with command line, which would start new Thunderbird message with attached file.

At the moment I already know how to do that:

thunderbird -compose to="test@foo.com",subject="testsubject",body="testbody",attachment="**file:///home/username/testattachment.foo**"

But the thing is I want to attach file, which would have different name everytime, for example: invoice-174.pdf

My logic told me to write:
thunderbird -compose to="test@foo.com",subject="testsubject",body="testbody",attachment="**file:///home/username/invoice-*.pdf**"

But this doesn't work. So, have you got any ideas?> 

---

### Post by anewguy on 2008-09-24
I have to warn you I don't know squat about shell scripts, but that is what you need I think.  You could then feed the filename in as a parameter when the script is run.  Someone may be able to help you with that or look for how-to's on bash scripting.

Dave :)

---

### Post by Orange_and_Green on 2008-09-24
Hello ledibri :)

If I were you I'd try using shell expansion... does this work?

[EDIT: this is the correct command]
thunderbird -compose to="test@foo.com",subject="testsubject",body="test body",attachment="file://$(ls /home/username/invoice-*.pdf)"

Basically, in bash, the syntax $(command) expands to the output of the command...
I found that ls spits out the full path, not just the file name. Oops... should work now. Can you confirm?

---

### Post by anewguy on 2008-09-24
I found this sample in a bash script tutorial.  Perhaps you can use it as a basis to input the file name and then do your process.  You would need to execute this via a launcher as a terminal application.
 
               #!/bin/bash
                echo Please, enter your firstname and lastname
                read FN LN 
                echo "Hi! $LN, $FN !"

The result I think would look something like this:

#!/bin/bash
echo Please enter the file name to attach
read MYFILEPATH
thunderbird -compose to="test@foo.com",subject="testsubject",body="test body",attachment="file:$MYFILEPATH"

If the path is always the same you could hard-code it and just take in the file name.


EDIT:  forgot to add - do this in an editor, save as a file - probably with a .sh extension, then create the launcher to run the script with the launcher type of a terminal application.

EDIT-EDIT:  I tested this from the command line and it creates the message with the attachment, but it doesn't automatically send it - perhaps there is another command line switch to do that (I've never looked).  You have to chmod 755 the file before you can execute it:  chmod 755 myscript.sh

To test in command line:

when in the folder the script is in, ./myscript.sh

You should be able to set this up as a launcher, but there may be something that has to preface the script name to tell it to use the bash shell. 

EDIT-EDIT-EDIT:  I created a laucher of type terminal application and it runs fine.  You do have to enter the full path with the filename when prompted or it thunderbird bombs out with an error message.  If the files are to all be from the same folder, just hard code it in front of the filename.

dave :)

---

### Post by ledibri on 2008-09-24
Orange_and_Green, I wrote the thing you gave, but it doesn't work. In Attachments I see invoice*.pdf) and clicking on it doesn't do anything.

---

### Post by Orange_and_Green on 2008-09-24
Sorry, my mistake. Try

thunderbird -compose to="test@foo.com",subject="testsubject",body="test body",attachment="file://$(ls /home/username/invoice-*.pdf)"

---

### Post by ledibri on 2008-09-24
Orange_and_Green, it still gives the same result.

Maybe I explained bad. So, again, what I want to do: I'll create file on desktop, then with launcher I open a "compose message" window with attached file. File name will be different everytime, for example: today invoice-147.pdf, tomorrow invoice-148.pdf (there will be one file on desktop)

---

### Post by Orange_and_Green on 2008-09-24
EDIT:

Try this: create an empty file called "thunderbird.sh" in your home (or any other directory).

Open it with text editor and type:

```
#!/bin/bash
thunderbird -compose to="test@foo.com",subject="testsubject",body="tes t body",attachment="file://$(ls /home/username/Desktop/invoice-*.pdf)"
```

Please replace "username" with your actual username.
Also, right-click it, select Properties->Permissions and check "execute"

Then create a launcher that points to this file.
Any luck now?

---

### Post by anewguy on 2008-09-24
Just change the script I already posted to point to the directory that will contain these files, set up the launcher and it runs fine.  The ls of the directory for all pdf files is not going to allow you to put a single attachment in if there is more than 1 pdf file in the directory.

---

### Post by ledibri on 2008-09-24
Oh, now I see too, it works :-). Actually, it's ok with Desktop, just the problem is it works (:-)) with command line, but it doesn't work when I write the same command in launcher.

---

### Post by Orange_and_Green on 2008-09-24
I edited my post. I think the best way is to create a script, set it as executable, and link the launcher to it (or double-click the script directly ;))

---

### Post by anewguy on 2008-09-24
> **ledibri said:**
> Oh, now I see too, it works :-). Actually, it's ok with Desktop, just the problem is it works (:-)) with command line, but it doesn't work when I write the same command in launcher.

For either choice, you must edit a file and put the command in it, then make the launcher point to the file.  

Orange_and_Green:  I tried your way from the command line first, pointing to my Documents folder since it contains multiple pdf files and made the filename *.pdf.  All my test did was pick up the last pdf file in the folder - no choice was given as to which pdf file I wanted.  Perhaps there is an error in your post.  The only reason I mention this is that given a single pdf file in the folder, as the poster has mentioned, it should work.  However, if multiple PDF files are in the folder no choice is given.  Your way would allow total automation if there is only 1 file - my way requires a file name be given.  While I think mine might be more flexible (:>) your way does seem to fit the ops problem if he sticks with just a single pdf file in the folder.

Dave :)

---

### Post by ledibri on 2008-09-24
> **Orange_and_Green said:**
> EDIT:

Try this: create an empty file called "thunderbird.sh" in your home (or any other directory).

Open it with text editor and type:

```
#!/bin/bash
thunderbird -compose to="test@foo.com",subject="testsubject",body="tes t body",attachment="file://$(ls /home/username/Desktop/invoice-*.pdf)"
```

Please replace "username" with your actual username.
Also, right-click it, select Properties->Permissions and check "execute"

Then create a launcher that points to this file.
Any luck now?

I did this and I get "There was an error launching the application.

Details: Failed to execute child process "/home/ledibri/thunderbird.sh" (Permission denied)"

---

### Post by anewguy on 2008-09-24
> **ledibri said:**
> I did this and I get "There was an error launching the application.

Details: Failed to execute child process "/home/ledibri/thunderbird.sh" (Permission denied)"

You need to do this in a terminal:

chmod +x /home/ledibri/thunderbird.sh

-or-

chmod 755 /home/ledibri/thunderbird.sh

That will make the file executable and get rid of the permissions error.

---

### Post by ledibri on 2008-09-24
> **anewguy said:**
> You need to do this in a terminal:

chmod +x /home/ledibri/thunderbird.sh

That will make the file executable and get rid of the permissions error.

Thanks everyone! Now it works! If there is more than 1 file in folder, it doesn't.

---

And now I will try Dave's solution.

---

### Post by anewguy on 2008-09-24
> **ledibri said:**
> Thanks everyone! Now it works!

---

And now I will try Dave's solution.

Be aware as I posted in a previous message - Orange_and_Green's way will fully automate the process as long as (1) there is only 1 pdf file in the folder -or- (2) the pdf you are interested in is the last in the folder.

My way does not fully automate the process, but gives you the chance to enter the file name.

So, if you are looking for full automation, use Orange_and_Green's way and remember just to keep a single pdf in the folder being searched.


Hope that's of some help to you.

Orange_and_Green:  Please don't take anything I said in a bad way - your way works great especially for full automation!

Dave :)

EDIT:  Please be sure to click on the "star" by one of Orange_and_Green's posts to thank him for helping you.

---

### Post by Orange_and_Green on 2008-09-24
> **anewguy said:**
> Please don't take anything I said in a bad way - your way works great especially for full automation!

Dave :)

Dear Dave,

I cannot see how I could take your posts in a bad way. Ubuntu (and Open Source in general) also means diversity, and choice. Different people find different solutions to the same problem, and this diversity enrichens the whole community. We both tried to help the OP and found two different solutions, so (s)he and any other people interested in the problem can choose what best fits their needs. And you deserve a star just as much as I do:KS

The scenario where there are more than one pdf on the desktop requires a more complex script indeed to be fully automated... I suppose that first I would need to know what behaviour the OP would like to have in such a case:
1) Attach all the files
2) Attach only the most recent one
3) Attach only the latest one
4) .....

I am happy if I could help anyone... or even if I couldn't, as I learned a new thing about scripting today and that has enrichened me.

:)I love Ubuntu philosophy:)

---

