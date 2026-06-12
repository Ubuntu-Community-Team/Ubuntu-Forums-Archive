---
title: "Controlling a robot arm: Interactive Python Program"
date: 2011-07-07
forum: Programming Talk
---

### Post by Call on 2011-07-07
Can you give me some advice on how to do an interactive python program? or point me to a good tutorial?

Let me explain (sorry for the noob question, but googling "python interactive" results in a lot of information about the interactive shell and it is not what I mean).

For sake of clarity, let do an example and say I want to control a robot arm via a python program.

So I built a nice library with all the stuff needed to communicate with the arm, and a nice function that when called
```
set_arm_position(5.0)
```move the arm in the position 5.

What is the best way to allow the user to set the position of the arm?

On one side, I could do a script with an argument and let the user call it in the Linux terminal.
This seems easy, but maybe the arm require some initialization and I do not want to initialize it every time.

So instead I could do a program with a loop that continuosly check for user input, but this does not seem easily upgraded to more complicated setup.

What about having all the parameters in a config file and having the program checking for change in the file?

In the end I would like something that can be used from the command line, but maybe later I would like to add some gui frontend.


On other words: what is the best way to write a Python program whose parameters can be controlled by the user or by other programs? In particular I would like a way that can allow, in a later moment, scripting
or controlling trough a gui.

Hoping you did undestand my question, do you have any suggestion?

---

### Post by pafoo on 2011-07-07
Hmm, maybe create a function that asks for user input, then that function will call to the class.function of your robot arm move. That way you only have to edit the class, you can also set your class to be editable by the user via get and set to do changes or adjustments of the movements on the fly

---

### Post by ve4cib on 2011-07-07
If you use a loop that reads input from the user over stdin (and keeps going until an exit command is sent; EOF is a nice easy one) then it's very easy to use pipes to allow for scripting/control by a GUI.

Alternatively, if you have a common backend library you can easily create both a GUI and a console application using that same backend, but with different interfaces for interacting with the user.

---

