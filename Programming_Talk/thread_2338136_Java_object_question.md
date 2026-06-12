---
title: "Java object question"
date: 2016-09-25
forum: Programming Talk
---

### Post by rogueleader12345 on 2016-09-25
Hello again all!

It's been quite a few years, but post-Army and finally in college I am hoping to get back into the swing of things and continue delving into Ubuntu like I once used to!

That being said, my return icebreaker, so to speak, is probably a very basic question but one that has been annoying me since my last Java assignment, and my teacher was no help besides "sounds like you're trying and trying and it isn't working, I usually go back and start over" which didn't answer my question.

Let me set the scene. We had an assignment that tasked us to create a Plate class that stored a two dimensional double array of size 12x12 that held the temperature of the "plate" once it had reached a steady state (temperature did not vary by greater than .1 at any point between 2 times). This is designed to represent a thermal modeling, where he gave us an input file of 4 numbers separated by a comma that were to be used as the temperatures to be "applied" to the plate at 12, 3, 6, and 9 o'clock, respectively. The actual plate is only 10x10, with the extra rows and columns used to store the applied temperatures. The state of the plate at t+1 is then simulated by averaging the temperatures of the square in question with its four neighbors. We were to run the simulation until the plate was in its "steady state", and the method "processTempsFromFile" (the only one he was testing for) was to produce an output of a Plate array containing the steady state plate objects (one for every line in the file he ran). Each plate was to be initialized at 68 degrees to begin with.

Now, to my issue.

My logic approaching this was to create three plates per line in the file (contained in a loop that repeated the entire process while there was another plate to simulate): plateInitial, plateTest, and plateResults. My plate class contained a class variable of double[][] values, but was not static so that it was an instance variable. I pulled the temperatures from the file and placed them in an array of their own. Entering my processing loop, it pulled the temperatures for the respective plate and passed them as arguments into my Plate constructor (in which initializePlate was a method) and that worked just fine, setting up the plate as desired. It then assigned plateIntial to plateTest, and entered a while loop while !isSteady (a boolean I set up), then ran my simulation method on plateTest and store the results to plateResults.values, also worked fine. It then passed plateTest and plateResults into my isSteadyState method, which returned false. I then assigned plateResults.values to plateTest.values, and the loop starts again. However, on the second iteration of the loop, my boolean would flip to true because it was comparing the same array. I brought this up in class, to which I learned that java was not copying the array from one object to the other, but rather was linking one to the other. So I went back and refactored my program using .clone() as my instructor suggested, which still didn't work. I then asked him how I could accomplish what I wanted to (copying the actual object plateResults and overwriting plateTest with it) to which he told me I basically needed to redo the whole thing. In the end, I ended up having to completely rewrite the program using a ton of nested loops to overwrite array values at every data point any time it needed edited. So my question to you is how can I overwrite one object with a different instance of the same object, as I was trying to do? Or can you even do it? All my instructor said is "you could probably brute force your way into getting your logic to work". Any ideas? Thanks in advance!

-rogueleader

---

### Post by trent.josephsen on 2016-09-25
Thanks for asking! I'll do my best, but I apologize for any language errors -- my Java's a bit *Rusty*.

So, if I understand your problem correctly, you wrote something like this:
```
Plate plateTest = plateInitial;
Plate plateResults = new Plate(...);
boolean isSteady = false;
while (!isSteady) {
    // compute the new state of the plate and store it in plateResults

    if (isSteadyState(plateResults, plateTest)) {
        isSteady = true;
    }
    plateTest = plateResults; // this is the problematic line
}
```

So far so good? Okay. You already found out that that "problematic" assignment doesn't copy plateResults, but just makes plateTest an alias to it. (Aliasing is programmer jargon for when two or more references (variables, for instance) refer to the same thing.) That means the next time through the loop plateTest and plateResults refer to the same object and so isSteadyState always returns true. (Correct me if I'm not getting this right.)

One way to solve this is what you did: instead of assigning one to the other, which causes aliasing, write over plateTest.values with the contents of plateResult.values. You can write a method to do it but it does require nested loops. But there's another way. Assignment with the = operator just points plateTest at the **old** Plate. The opposite of old is **new**, and the **new** operator is how you *create* any kind of object, so we can do that -- create a new object to store the results in each time through the loop.

```
Plate plateTest = plateInitial;
boolean isSteady = false;
while (!isSteady) {
    Plate plateResults = new Plate(...); // create a new plate (once per iteration)
    // compute the new state of the plate and store it in plateResults

    if (isSteadyState(plateResults, plateTest)) {
        isSteady = true;
    }
    plateTest = plateResults; // this is fine now because plateResults will point to a new plate at the beginning of the next iteration of the loop
}
```

Make sense? The main disadvantage of this approach is it uses more memory, because on every loop iteration you have to allocate another 12x12 array (until the garbage collector runs -- but I don't want to get distracted by that). The advantage is that it might be easier to read and it's definitely shorter.

As far as I know there is no "copy/move from" or "replace" functionality in Java, that would allow you to replace the contents of one object with another; but there is [System.arraycopy](https://docs.oracle.com/javase/7/docs/api/index.html?java/lang/System.html), which I expect you could use to get rid of at least one of those loops -- don't ask me how though!

Hope this helps.

---

