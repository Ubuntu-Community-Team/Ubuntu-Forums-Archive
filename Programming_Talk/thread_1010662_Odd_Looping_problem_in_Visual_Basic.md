---
title: "Odd Looping problem in Visual Basic"
date: 2008-12-14
forum: Programming Talk
---

### Post by Orange_Ribbon on 2008-12-14
Okay,  this is for a speak and spell program,  you input a work, and it plays the sound files for the letters.  Just something goofy I started when I was bored.  I am just learning to program, and my intro class is in VB. 

here is the code I am trying to figure out.

```
Private Sub btnPlay_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPlay.Click
        Dim timeout As DateTime = Now.AddSeconds(3)
        loc = txtRead.Text
        X = loc.Length
        Y = 0

        Do While Y < X
            If loc.Substring(Y, 1) = "A" Then
                My.Computer.Audio.Play("C:\wav\a.wav")
                Do Until Now > timeout
                    Application.DoEvents()
                Loop

            ElseIf loc.Substring(Y, 1) = "D" Then
                My.Computer.Audio.Play("C:\wav\D.wav")
                Do Until Now > timeout
                    Application.DoEvents()
                Loop
                
            End If
            Y = Y + 1
        Loop


    End Sub
```

So basically I am just getting the amount of charecters, in the string, and and the comparing it to 0, and adding 1 per loop.  Now basically if I type in DAD I get the two D waves.  ADD gives me an A and D  and ADA gives me two As.  For some reason I am not getting that second letter.  I have tried increasing the pause to as much as 10 seconds, but same results.  

Hmmm I should make it "A" or "a" while I am looking at this.

---

### Post by mssever on 2008-12-14
> **Orange_Ribbon said:**
> So basically I am just getting the amount of charecters, in the string, and and the comparing it to 0, and adding 1 per loop.  Now basically if I type in DAD I get the two D waves.  ADD gives me an A and D  and ADA gives me two As.  For some reason I am not getting that second letter.  I have tried increasing the pause to as much as 10 seconds, but same results.
[COLOR=Silver]I don't know VB, but I'm guessing the Loop keyword means to go immediately to the next iteration of the loop. If that's correct, then Y isn't getting incremented properly. Try dropping the Loop statements under the If and Else If since they're unnecessary.

Of course, if my guess about Loop is wrong, then my whole answer is probably wrong, as well.[/COLOR] 

EDIT: Never mind. I misread your code.

In VB, is = a boolean operator? In many languages, you need to use == in if statements and the like to get a boolean test. You've only got a single = which might be a problem.

---

### Post by kjohansen on 2008-12-14
a single "=" is a comparison operator in VB...

---

### Post by pp. on 2008-12-14
You should add some debugging aids into your function. Why not print the values of y, loc and loc.substring(y.1) at the start of each loop?

---

### Post by Jonas thomas on 2008-12-14
> **Orange_Ribbon said:**
> Okay,  this is for a speak and spell program,  you input a work, and it plays the sound files for the letters.  Just something goofy I started when I was bored.  I am just learning to program, and my intro class is in VB. 

here is the code I am trying to figure out.

```
Private Sub btnPlay_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnPlay.Click
        Dim timeout As DateTime = Now.AddSeconds(3)
        loc = txtRead.Text
        X = loc.Length
        Y = 0

        Do While Y < X
            If loc.Substring(Y, 1) = "A" Then
                My.Computer.Audio.Play("C:\wav\a.wav")
                Do Until Now > timeout
                    Application.DoEvents()
                Loop

            ElseIf loc.Substring(Y, 1) = "D" Then
                My.Computer.Audio.Play("C:\wav\D.wav")
                Do Until Now > timeout
                    Application.DoEvents()
                Loop
                
            End If
            Y = Y + 1
        Loop


    End Sub
```

So basically I am just getting the amount of charecters, in the string, and and the comparing it to 0, and adding 1 per loop.  Now basically if I type in DAD I get the two D waves.  ADD gives me an A and D  and ADA gives me two As.  For some reason I am not getting that second letter.  I have tried increasing the pause to as much as 10 seconds, but same results.  

Hmmm I should make it "A" or "a" while I am looking at this.

Ok... So I guess this is .NET. I'm only into VB6 but I thought I'd some critique.
loc is undeclared.. Vb6 would let you get away with that but it will only if you specified "option explicit"  Does anyone know if .net has that??
You should always declare your variables before you use them (imho).  It will only cause you pain in the long run.  Basically if you don't declare your variables you'll wind up having a really stupid bug in your code that will take you a long time to figure out...

I think your on to something with the "A" or "a".  I don't know how case sensitive .net is but that was a rude awakening for me, when I started with linux.  So I guess the easiest thing is to see what is listed in your directories either "A.wav" or "a.wav" and match it.

I think you might be barking up the wrong tree with the timeout thing.. I'd get rid of it.

One other suggestion.
Pull out each character from your text and convert it to lower case or upper case as required.

create a string for the file name and build the file patch
file_name = "C:\wav\" & Your_letter & ".wav"
My.Computer.Audio.Play(file_name)

---

### Post by nvteighen on 2008-12-14
> **pp. said:**
> You should add some debugging aids into your function. Why not print the values of y, loc and loc.substring(y.1) at the start of each loop?
Because VB hardens debugging. You'll have to use a message box or something like that, otherwise using "Print" will disrupt the Form.

@OP:
What VB are you using? In VB6 I'd have used a Timer object instead... Anyway, I guess the issue is at the inner-loops where you check if 3 secs have passed or not. Are you sure that Now is incremented each time it is accessed?

---

### Post by pp. on 2008-12-14
> **nvteighen said:**
> Because VB hardens debugging. You'll have to use a message box or something like that, otherwise using "Print" will disrupt the Form.

Then, it's not "debugging" but guessing games.

I still think OP would be best served by reducing the program to the bare bones. Actually, playing the sound files is not needed for defining the logic of the program and is less than helpful for finding where the logic appears to fail.

---

### Post by nvteighen on 2008-12-14
> **pp. said:**
> Then, it's not "debugging" but guessing games.


That's one of the reasons why VB is horrible.

---

### Post by Jonas thomas on 2008-12-14
> **nvteighen said:**
> That's one of the reasons why VB is horrible.

Just to clarify, I believe Vb.net is horrible.. VB6 bless it's little going obsolete soul was awesome. (imho anyway)

---

### Post by Orange_Ribbon on 2008-12-14
Okay,  so I had it spit Y to a messagebox, and the Delay was only working once, and then it would spit the messageboxs out as fast as I hit okay.  Since the the program was trying to play the wave really fast it would only play the first (when the delayed worked) and last wav file when it wouldn't be interrupted.  

Now I have to cut up the recording of my friend singing the phonetic alphabet, and take out my horrible ones. 

As far as what version it was,  they are up to 9.  I kinda don't like the fact that you can't save as a lower version,  just upgrade older files to this.  I got it when I went to the MS release event in PA, and I can't use it for class, because in class we use 8.

---

### Post by pp. on 2008-12-14
Now that the cause of the problem is known, you know where to look for a cure. My suggestion is to search for a means to play a sound which returns control to the application only when the playing of the sound has reached the end of the sound file.

If VB can't do that, there are perhaps other tools which can.

---

