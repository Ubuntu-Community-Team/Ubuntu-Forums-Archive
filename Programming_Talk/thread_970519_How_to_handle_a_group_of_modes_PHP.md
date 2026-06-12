---
title: "How to handle a group of modes PHP"
date: 2008-11-04
forum: Programming Talk
---

### Post by scragar on 2008-11-04
I have 5 or 6 different modes for a class I am constructing, and since each mode can be on or off, 1 or 0, I decided to implement this with a single integer, rather than a number of boolean values, this works rather well, I can get a values by using:
```
$this->mode & self::MODE_**settingName**_ON
``` which does work correctly, however I was hoping to be able to turn multiple modes on or off at the same time, which is where my problem is occuring, I have no idea what to set the off mode to in order to allow the maths to work, I think it's better to demonstrate this:
```
NAME	ON	OFF
a	1	-1
b	2	-2
c	4	-4
d	8	-8
```Changing multiple modes, I theorised, could be done by adding the values, so a+c+d = 13.

In testing I realised the flaw in this logic, turning d on( 8 ), then turning c off( -4 ) results in a value of 4, which means to turn c on. Does anyone have any ideas as to how I may best handle this situation(changing the values they represent is not hard right now, since they are not hard-coded anywhere in the script, so if it comes to using larger numbers or whatever I can change things fairly quickly)

---

### Post by Reiger on 2008-11-04
Essentially your using a bit mask. So, bitwise operators are the way to go. Something like:
[php]
$modus=0;

$mode1=1;  $mode2=2;
$mode3=4;  $mode4=8;
$mode5=16; $mode6=32;

function turnOn($value) {
self->modus = self->modus | $value; // turn on the bit in the modus
}

function turnOff($value) {
$value = ~ $value; // invert the value
self->modus = self->modus & $value; /* turn off the bit in the modus: the whole function can be rewritten as: self->modus= self->modus & (~ $value); */
}

function isOn($testMode) {
  return (self->modus & $testMode)==$testMode;
}

function isOff($testMode) {
  return (self->modus & $testMode)==0;
}

[/php]

See also: [http://www.phpbuilder.com/manual/en/language.operators.bitwise.php](http://www.phpbuilder.com/manual/en/language.operators.bitwise.php)

---

### Post by scragar on 2008-11-04
I know I can do that, I have no problems with that, my problem is that I wanted to be able to handle multiple modes in the same run, but it looks like I'll only be able to do multiple ons/offs at the same time, rather than all of them at once. Thanks for the help anyway.



EDIT: I think I have a solution, doubling the difference:
```
NAME	ON	OFF
a	1	-1
b	4	-4
c	16	-16
d	64	-64
```
then to test the values going back again I can do:
[php]function mode($mode = 0){
  for($i = 64; $i >= 1; $i /= 4){
    if($mode > 0){// positive, test on
       if($mode > $i/2){// turn mode on
         $mode -= $i;
         $this->mode = $this->mode | $i;
       }
    }else if($mode < 0){// negative, test off
      if($mode < -($i/2)){// turn off if on
        $mode += $i;
        $this->mode = $this->mode & (~ $i);
      }
    }else{// mode = 0, all done
      return $this->mode;
    }
  }
}[/php]But I've not had a chance to test this sufficiently yet.

---

### Post by mike_g on 2008-11-04
Out of curiosity, why do you need a negative off value? I cant see any benefit.

Negative values have bits set which will interfere with your mask when you 'and' them to check whether the 'on' value is set or not.

---

### Post by scragar on 2008-11-04
I don't need it, but since this class is going to be public I kind of need to assume that I'll be reciving emails from people asking silly questions, I am just hoping that having on and off options for all the modes will reduce those emails somewhat(atleast I'm hoping it will).

---

### Post by mike_g on 2008-11-04
I really think that you should be using an absence of the mode bit to represent the state being set to off. The negative values will screw up you bitmask when you try doing stuff like:
```
$this->mode & self::MODE_settingName_ON
```
I'm pretty sure that by doubling the values you have not fixed the problem. It only appears not to cause a problem with your test data you used.

Edit: to explain this better the binary representation for the number -1 using twos complement would have all bits set. When 'anded' this would give you results telling you that all modes are on.

---

### Post by Reiger on 2008-11-04
> **scragar said:**
> my problem is that I wanted to be able to handle multiple modes in the same run[/php]

Right either I'm misunderstanding something very badly, but to me that sounds like you want to give it a bit mask (for multiple modes) to turn on or off at the same time. Which is what my code should allow for. (All you have to do is passing something like: ($mode1 | $mode2). ) Which means.. :confused:

---

