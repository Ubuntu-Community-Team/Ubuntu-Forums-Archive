---
title: "Executing a function in one program from another ?!?"
date: 2007-06-07
forum: Programming Talk
---

### Post by renzokuken on 2007-06-07
Hi, 

first off a little background as to what i'm doing. I have a motorised X-Y stage which i have written a program to control through the serial port using VB.NET (hacked about some demo source code that came with the stage).

I have used buttons to send data to the stage to get it to move to the desired coordinates.

I now have to write a program in Varian ADL (Varian is the spectrometer make and ADL is its own shell built into its software) to move the stage to a point, do a scan, move to the next point, do a scan etc. in a completely automated fashion.

I am having a hard time figuring out how to get ADLShell to communicate with serial ports, and so i was wondering, is it possible to get the ADLShell to execute one of the buttons on my external VB.NET program?

Does that make sense?

ADL is pretty much VB with a few built in functions specifically for the spectrometer. The manual mentions "SAX Basic" whatever that is.

Any ideas?

Thanks

Rob

---

### Post by ssam on 2007-06-07
[XML-RPC]("http://en.wikipedia.org/wiki/XML-RPC") is designed for that sort of thing, and should work between many programming languages (though i have only used it python to python).

[http://www.xmlrpc.com/directory/1568/implementations](http://www.xmlrpc.com/directory/1568/implementations) is a list of implementations.

---

### Post by renzokuken on 2007-06-08
thanks for the reply ssam, but that looks way beyond my capabilities.....im some what of a n00b here. i've been thrown in the deepend by my supervisor, i'm a chemist, not much of a programmer.

i found this in the manual for ADL Shell

> Cary ADL has the ability to launch other applications. In DOS this was done through the Spawn_Prog command. In the new environment it is through the SHELL command. For example to launch the windows calculator run the following.

```
Sub Main  X=Shell("Calc")            'run the calc program
              AppActivate X SendKeys "%R"             'restore calc's main window
             SendKeys "30*2{+}10=",1                  'results in 70
End Sub
```

Talking to the program is done with the SendKeys command. This allows (as its name indicates) to send key strokes to the application. No information can be obtained back from the aplication this way.

They also mention DDE linkage. Could something like the above be used to activate (i.e. press a specific button) in my external program?

thanks

---

### Post by nerdzero on 2007-06-08
Well I've never used ADL or SAX Basic but I've done plenty of VB6 programming.

You can use SendKeys to "push" buttons on another form.  You may or may not be aware that if you place a **&** character in the caption of your button, the letter immediately following it becomes a hotkey.  

So, if you have buttons in your VB form called "Move Left", "Move Right" or whatever, you can change the captions to "Move &Left" and "Move &Right" to make ALT+L and ALT+R press the buttons.

Now, in your ADL program (assuming the syntax is like VB) your code would be something like this...

```
Sub Main

  Dim dblTaskID as double

  ''' Start your VB program
  dblTaskID = Shell("[path to your program]\[yourprogram.exe]", vbNormalFocus)

  ''' Activiate the VB form, may need some delay code here since 
  ''' Form may not be visible by the time we reach this line.
  AppActivate dblTaskID

 ''' Move left
  SendKeys "%L", True

  ''' Move right twice
  SendKeys "%R%R", True

  ''' close your VB program (Send ALT+F4)
  SendKeys "%{F4}", True

End Sub
```
Of course I would NOT recommend doing your final version this way.  You can just use this as a temporary solution.  SendKeys is not 100% reliable when paired with asynchronously executing functions such as Shell.  You will have to add a lot of workarounds and delay loops to get your timing down in some cases (although it will probably work 90% of time).

Ideally you'd want to convert your VB program to an assembly you can reference with a public class you can instantiate in your ADL program.  Then you can do something like this...
```

Sub Main

  Dim objStage as MyStageClass

  set objStage = New MyStageClass

  objStage.Initialize [some parameters]

  objStage.MoveLeft

  objStage.MoveRight
  objStage.MoveRight

  Set objStage = Nothing

End Sub
```

Of you course, you'd have to move all the code in your buttons to methods of your class and again I don't know anything about ADL so not sure how easy it is to reference outside libraries.  DDE stands for Dynamic Data Exchange and is a protocol for applications to talk to each other.  It's kind of tough to do in VB and I wouldn't recommend it for a newbie.  Hope that helps!

---

### Post by renzokuken on 2007-06-11
thanks for the reply nerdzero. i think i understand the first section of code so i may play around with that.

upon further reading online, i found another manual for my equipment which i wasnt given originally that details briefly and ADL function to communicate with RS232 which may make it even easier.

i'm going to have a play around with the ADL serial communications this week and see if i can move my stage with it. it would be much easier to have one program (macro) to control both the stage and the spectrometer.

no doubt i'll be back asking more questions later.

specifically about HEX codes. i may start another thread about that though so as to not get confused.

---

