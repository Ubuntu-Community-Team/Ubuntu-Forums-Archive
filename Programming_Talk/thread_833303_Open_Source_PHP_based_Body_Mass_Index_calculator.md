---
title: "Open Source PHP based Body Mass Index calculator"
date: 2008-06-18
forum: Programming Talk
---

### Post by 7Priest7 on 2008-06-18
No Code For Ubuntu Forums

---

### Post by kool_kat_os on 2008-06-18
do you have an example set up?
I dont have my server set up yet


EDIT: nevermind...forgot to click on the links

---

### Post by kool_kat_os on 2008-06-18
im underweight....:confused:

---

### Post by melopsittacus on 2008-06-18
Hi!

Just some remarks:
 - why do you check if the user has supplied their weight but do not check if they supplied their height?
 - as the outputs for the two cases are almost a same, I think you could combine the common sections to be always printed
 - I think it is a little too well commented :D

---

### Post by -grubby on 2008-06-18
At the end: 

[php]
else if($BMI < 40 && BMI > 30) // If there BMI is between 30 and 40 [/php]

You seem to be missing a dollar sign on that variable.

Also, I scored 18.3 on that BMI calculator

---

### Post by 7Priest7 on 2008-06-18
> **melopsittacus said:**
> Hi!

Just some remarks:
 - why do you check if the user has supplied their weight but do not check if they supplied their height?
Lazieness As it were I would have to factor if they did it all in inches or all in feet which would require more ifs...
> 
 - as the outputs for the two cases are almost a same, I think you could combine the common sections to be always printed
Indeed... You speak of the header and such... I agree... I did it to some degree with the $script var and the $form var> 
 - I think it is a little too well commented :D
Better safe than sorry there may be people barely learning to code that browse my code... 

And Thanks for the comments

Alex

---

### Post by 7Priest7 on 2008-06-18
> **nathangrubb said:**
> At the end: 

[php]
else if($BMI < 40 && BMI > 30) // If there BMI is between 30 and 40 [/php]

You seem to be missing a dollar sign on that variable.

Also, I scored 18.3 on that BMI calculator

Thanks I did not notice that since I am "perfect weight" and my friend is "overweight" None of my freiends are Morbidly Obese

BMI calculator has been tested pretty well if you really believe it is wrong you could test your BMI on other calcs on the web...

Thanks

Alex

---

### Post by Phenax on 2008-06-18
Just a note; BMI is not a great source to use to tell if you are underweight/overweight/obese/normal/etc. Google it if you want more information.

---

### Post by LaRoza on 2008-06-18
> **nathangrubb said:**
> 
Also, I scored 18.3 on that BMI calculator

I got 18.9 (not on that, I didn't bother to run it, but on an old app I made)

In case anyone is slightly interested:

It works with feet/inches/metres and lbs/kg. It defaults to metres and kg.
[php]
#!/usr/bin/python
import sys
import math

class BMI:
    """Created a BMI object and calculates the BMI using the units specified (feet/ft or inches/in for height and lbs/lb for weight) or uses the standard SI units for the calculation."""

    def __init__(self,weight,height):
        if height.endswith("ft") or height.endswith("feet"):
            self.height = float(height.split("f")[0]) * 12
        elif height.endswith("in") or height.endswith("inches"):
            self.height = float(height.split("in")[0])

        if weight.endswith("lbs") or weight.endswith("lb"):
            self.weight =  float(weight.split("lb")[0]) * 703
        else:
            self.weight = float(weight)

        self.bmi = self.weight / (self.height * self.height)


    def test(self):
        """"Returns a tuple of the BMI and Status"""
        if self.bmi >= 40:
            self.status = "Morbidly Obese"
        elif self.bmi >= 35:
            self.status = "Clinically Obese"
        elif self.bmi >= 30:
            self.status = "Obese"
        elif self.bmi >= 25:
            self.status = "Overweight"
        elif self.bmi >= 18.5:
            self.status = "Normal"
        elif self.bmi >= 16.5:
            self.status = "Underweight"
        elif self.bmi < 16.5:
            self.status = "Severely underweight"

        return (self.bmi,self.status)

if __name__ == "__main__":
    if len(sys.argv) == 3:
        me = BMI(sys.argv[1],sys.argv[2])
        status = me.test()
        print "Your BMI is: %f, you are %s" % status
    else:
        print "Give weight and height and the units if they are not SI"
[/php]

```

/media/STORAGE/code/pythonCode/bmi$./bmi.py 140lbs 72in
Your BMI is: 18.985340, you are Normal
/media/STORAGE/code/pythonCode/bmi$

```

---

### Post by -grubby on 2008-06-19
> **LaRoza said:**
> I got 18.9 (not on that, I didn't bother to run it, but on an old app I made)

In case anyone is slightly interested:

It works with feet/inches/metres and lbs/kg. It defaults to metres and kg.
[php]
#!/usr/bin/python
import sys
import math

class BMI:
    """Created a BMI object and calculates the BMI using the units specified (feet/ft or inches/in for height and lbs/lb for weight) or uses the standard SI units for the calculation."""

    def __init__(self,weight,height):
        if height.endswith("ft") or height.endswith("feet"):
            self.height = float(height.split("f")[0]) * 12
        elif height.endswith("in") or height.endswith("inches"):
            self.height = float(height.split("in")[0])

        if weight.endswith("lbs") or weight.endswith("lb"):
            self.weight =  float(weight.split("lb")[0]) * 703
        else:
            self.weight = float(weight)

        self.bmi = self.weight / (self.height * self.height)


    def test(self):
        """"Returns a tuple of the BMI and Status"""
        if self.bmi >= 40:
            self.status = "Morbidly Obese"
        elif self.bmi >= 35:
            self.status = "Clinically Obese"
        elif self.bmi >= 30:
            self.status = "Obese"
        elif self.bmi >= 25:
            self.status = "Overweight"
        elif self.bmi >= 18.5:
            self.status = "Normal"
        elif self.bmi >= 16.5:
            self.status = "Underweight"
        elif self.bmi < 16.5:
            self.status = "Severely underweight"

        return (self.bmi,self.status)

if __name__ == "__main__":
    if len(sys.argv) == 3:
        me = BMI(sys.argv[1],sys.argv[2])
        status = me.test()
        print "Your BMI is: %f, you are %s" % status
    else:
        print "Give weight and height and the units if they are not SI"
[/php]

```

/media/STORAGE/code/pythonCode/bmi$./bmi.py 140lbs 72in
Your BMI is: 18.985340, you are Normal
/media/STORAGE/code/pythonCode/bmi$

```

You can put dots in Python variables? I never knew that. I don't know why I just assumed that you can't either. Thanks for that, even if it wasn't intentional at all

EDIT: Maybe I'm wrong. Self is a reserved Python word after all. I'll go try it and see what happens in the python interpreter

EDIT2: Well of course you can't. The dot.variable thing is reserved for functions..

---

### Post by supirman on 2008-06-19
BMI has zero use.  For example - I'm 5'7" 220lbs and it says I'm close to clinically obese... Look at my avatar, it will show you how useful BMI really is.

---

### Post by NilsHG on 2008-06-19
the bmi calculator is far from usefull until it accepts metric units aswell :lolflag:

---

### Post by LaRoza on 2008-06-19
> **NilsHG said:**
> the bmi calculator is far from usefull until it accepts metric units aswell

Mine does that by default (you don't need to specify units)

> **nathangrubb said:**
> 
EDIT: Maybe I'm wrong. Self is a reserved Python word after all. I'll go try it and see what happens in the python interpreter

EDIT2: Well of course you can't. The dot.variable thing is reserved for functions..
self isn't reserved (I think) it is just a convention. The first parametre to a method is the object itself. (Look at the contstructor) It can be named anything. self.<name> just references data in the class.


> **supirman said:**
> BMI has zero use.  For example - I'm 5'7" 220lbs and it says I'm close to clinically obese... Look at my avatar, it will show you how useful BMI really is.

BMI has good use if you know the person. It is skewed when dealing with aging people, athletes and other people. Because it requires you to know the person, that doesn't make it useless.

---

### Post by 7Priest7 on 2008-06-30
> **supirman said:**
> BMI has zero use.  For example - I'm 5'7" 220lbs and it says I'm close to clinically obese... Look at my avatar, it will show you how useful BMI really is.

Indeed BMI cannot factor in things like Steroid Use as your image shows...

As a genral rule of thumb if you need to/want to check your BMI you  probably do not have ABs as you do...

Also Gender is not factored...

It is good to a degree but not always accurate...

But there are exceptions to everything


Hope I helped you grasp the concept

Priest

---

### Post by LaRoza on 2008-06-30
> **7Priest7 said:**
> Indeed BMI cannot factor in things like Steroid Use as your image shows...


I see no indication of anabolic steriod use (which is usually illegal) in that avatar.

BMI does fail in naturally musclar or larger people. Take someone like Paul Anderson, even ripped he weighed over 300 lbs, but he and heavily muscled people are not your typical person. The typical person is getting "fatter" it seems...

---

### Post by supirman on 2008-06-30
> **7Priest7 said:**
> Indeed BMI cannot factor in things like Steroid Use as your image shows...


My image implies steroid use?  Get a clue.  I've been lifting 5 days/week for 10 years.

---

### Post by LaRoza on 2008-06-30
> **supirman said:**
> My image implies steroid use?  Get a clue.  I've been lifting 5 days/week for 10 years.

Nice work :-)

(I guess my avatar implies crack use...)

---

### Post by -grubby on 2008-06-30
> **LaRoza said:**
> Nice work :-)

(I guess my avatar implies crack use...)

lol. I think mine implies that... I'm a beach

---

### Post by 7Priest7 on 2008-07-01
> **supirman said:**
> My image implies steroid use?  Get a clue.  I've been lifting 5 days/week for 10 years.

Hmm My bad... I overlooked the fact that you added nothing relevant to my code...
Furthermore I could care less about how you choose to spend your time...

"Get a clue"
^-- ROFL It is you who post barely relevant opinions on a programmers sub-forum

Your opinion on BMI is irrelevant to my code...

So unless you and the other members have something relevant to the code to say let this topic die...


Enough

Alex

---

### Post by LaRoza on 2008-07-01
> **7Priest7 said:**
> Hmm My bad... I overlooked the fact that you added nothing relevant to my code...
Furthermore I could care less about how you choose to spend your time...

Then don't make accusations of illegal activity. As for adding things to the code, he did. Coding isn't all about code, it is about solving problems. It makes no sense to have an app measure something meaningless, and there is a wide range of people to whom the BMI standard means little.

> 
ROFL It is you who post barely relevant opinions on a programmers sub-forum

It was only directly related to the subject... I don't see how that is "barely relevant".

> 
Your opinion on BMI is irrelevant to my code...

So unless you and the other members have something relevant to the code to say let this topic die...


You asked for the opinion. I am weary of your habit of posting your code and then attacking those who comment on it. In fact, I am less happy about you doing it to other people.

If you want to distribute code, there are many ways of doing that. Sourceforge, launchpad, and others, including privately maintained wiki's.

I have something to say about the code: It is invalid and messy and poorly designed. The functions are poorly named so far as you have to have comments explaining them. The mixture of all aspects of logic and design isn't near anything useful. I recommend you read this article: [http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller)

---

### Post by supirman on 2008-07-02
> **7Priest7 said:**
> Hmm My bad... I overlooked the fact that you added nothing relevant to my code...
Furthermore I could care less about how you choose to spend your time...

"Get a clue"
^-- ROFL It is you who post barely relevant opinions on a programmers sub-forum

Your opinion on BMI is irrelevant to my code...

So unless you and the other members have something relevant to the code to say let this topic die...


Enough

Alex

Wow, somebody has a grossly inflated view of their self worth... ](*,)

---

### Post by 7Priest7 on 2008-07-02
Wooo Idiots Post again...

Grats Supirman You are the dumbest person I have seen since I have been on this forum...

LaRoza Good Point... You guys do not deserve the privledge to give input on my code when you act like such morons...

I will discontinue posting code on these forums...

For that matter I am quitting these forums...

Far too many idiots like Supirman


Peace

Alex

---

### Post by Balazs_noob on 2008-07-02
> **7priest7 said:**
> You Guys Do Not Deserve The Privledge To Give Input On My Code


:lolflag:

---

### Post by CptPicard on 2008-07-02
Hmm... to introduce a bug into this that says *always* "you're too fat!" and then make it into some kind of MySpace app that appeals to teenage girls...

Presto, sudden increase in anorexia and teen suicides globally... :KS

---

### Post by supirman on 2008-07-02
> **7Priest7 said:**
> Wooo Idiots Post again...

Grats Supirman You are the dumbest person I have seen since I have been on this forum...

LaRoza Good Point... You guys do not deserve the privledge to give input on my code when you act like such morons...

I will discontinue posting code on these forums...

For that matter I am quitting these forums...

Far too many idiots like Supirman


Peace

Alex

Such an eloquent response...

---

### Post by LaRoza on 2008-07-02
> **7Priest7 said:**
> Wooo Idiots Post again...

Grats Supirman You are the dumbest person I have seen since I have been on this forum...

LaRoza Good Point... You guys do not deserve the privledge to give input on my code when you act like such morons...

I will discontinue posting code on these forums...

For that matter I am quitting these forums...

Far too many idiots like Supirman


There is no rule against being an idiot, only violating the Code of Conduct. 

I am not going to discuss this with you...I have written better PHP code and larger and more functional sites. I also wrote a better BMI app and posted it in this thread.

Have fun in the real world, where I hope you are either 7' tall or have a different personality.

I wanted to be an idiot also...

---

### Post by bapoumba on 2008-07-02
Please do not quote and reply to 7Priest7. The account is in the mod queue until admins have a look and get to the coffee burner machine in the back office.

---

### Post by LaRoza on 2008-07-02
> **bapoumba said:**
> Please do not quote and reply to 7Priest7. The account is in the mod queue until admins have a look and get to the coffee burner machine in the back office.

Well, his account is off the mod queue and has been moved to /dev/null...

I closed this thread to avoid any bumping.

---

