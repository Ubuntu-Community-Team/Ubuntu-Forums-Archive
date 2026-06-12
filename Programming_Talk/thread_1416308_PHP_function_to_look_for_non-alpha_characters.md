---
title: "PHP function to look for non-alpha characters"
date: 2010-02-25
forum: Programming Talk
---

### Post by blueshiftoverwatch on 2010-02-25
PHP has many built in variables, but not one that seems to do exactly what I want to do. I want an a function that is to letters as the [is_numeric]("http://us2.php.net/manual/en/function.is-numeric.php") function is to numbers.

I'm assuming that somewhere there exists the actual code that is used to create the 'is_numeric' function and in that code it probably lists the numbers "1234567890" and says that if it isn't one of those character than it isn't numeric. As well as some way to include hexadecimal numbers, but I'm not really interested in that.

Anyway, I figure that if I could find the code that makes up the 'is_numeric' function than I could just replace "1234567890" with "AaBcCcDd...etc" and basically have an 'is_alpha' function for what I am trying to accomplish.

Does anyone have a solution as to either how I could create my own function or use/modify an existing function to do this?

---

### Post by korvirlol on 2010-02-25
[PHP]function is_alpha($char){
     $valid = array('a', 'b', 'c', 'd', ...);

     return in_array($char, $valid);
}[/PHP]

---

### Post by blueshiftoverwatch on 2010-02-25
Thanks for the help, but I'm not sure if I'm applying this function correctly. As it doesn't appear to be working either when I type in one letter or multiple letters. As soon as the page is loaded it prints "Please enter alpha characters in the AlphaOnly field" and continues to do that even after I hit the submit button.

Here is my function that I put at the very beginning of where the PHP code starts:
```
            $valid = array('A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L',
                    'M', 'N', 'O','P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
                    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n',
                    'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z');
            
            return in_array($char, $valid);
        }
```

And here is where I'm trying to apply it:
```
        if(is_alpha($AlphaOnly) == false) {
            die("Must use alpha characters in the 'AlphaOnly' field");
        }
```
What exactly do the $char and $valid variables represent? Do I need to modify the 2nd block of code where I'm actually using the function to use those variables somehow, or vice versa?

---

### Post by Hellkeepa on 2010-02-26
HELLo!

Regular Expressions is what you want:
[php]function is_alpha ($String) {
    return preg_match ("/^[a-z\pL]*\z/ui", $String);
}[/php]
This one is set to accept regional charcters as well as empty strings, requires that the string is UTF-8 for use with charcters beyond a-z.

Happy codin'!

---

### Post by blueshiftoverwatch on 2010-02-26
For some reason neitiher of those functions work. I must be doing something wrong. I tried changing the $String varitables to $AlphaOnly as well, but to no avail.

---

### Post by Hellkeepa on 2010-02-26
HELLo!

Just tested my function, to verify that it works as advertized:
[php]php > function is_alpha ($String) {
php {     return preg_match ("/^[a-z\pL]*\z/ui", $String);
php { }
php > $string = "testingæøå";
php > var_dump (is_alpha($string));
int(1)
[/php]
If you could post the code where you're trying to use the function, as well as a "var_dump ()" of the variable you're testing, it'd be of much help in figuring out what the issue is.

Happy codin'!

---

### Post by blueshiftoverwatch on 2010-02-26
> **Hellkeepa said:**
> If you could post the code where you're trying to use
No need, I got it working. It was an error on my part for not having it some of my code in the right order.

---

