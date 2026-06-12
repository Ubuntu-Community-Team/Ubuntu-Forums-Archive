---
title: "php compiling"
date: 2010-01-13
forum: Programming Talk
---

### Post by newguy2010 on 2010-01-13
I think it will be clear when I explain. Suppose I have an html file and take data from it to process in another php file. When I compile the file (I use notepad++), it shows error on those variable names which contain data from the html file. 
For example,
[PHP]
$num=$_POST['number'];
[/PHP]

Compiler says there is error because there is undefined variable 'number'. How to correct this ?

---

### Post by EricDrijv on 2010-01-13
Are you using the method parameter in your forms?

form method="post"

Otherwise you can try the S_REQUEST function instead of the S_POST function

---

### Post by CyberJack on 2010-01-13
What output do you get when you make a var_dump of $_POST in the php file?
[PHP]
var_dump( $_POST );
[/PHP]

And can you show the code of your form used on the html page?

---

### Post by newguy2010 on 2010-01-13
My code is correct. I tested it out in the browser. I am running WAMP on my system. The error is when I tried to compile the php file separately. How to tell the compiler that the variables are from a html file ?

---

### Post by Hellkeepa on 2010-01-13
HELLo!

Considering that "number" is not a variable, but an index of the $_POST array (which is a variable), the error message doesn't make much sense.
I haven't used Notepad++ before, but generally PHP scripts are not compiled; They're interpreted at run time. So what the application does, I don't know. However, if you want us to be able to figure it out, please post all of the code pertaining to the form and its processing.

Happy codin'!

---

### Post by newguy2010 on 2010-01-13
I am sorry I think I am not explaining clearly enough. I will try again.
You are right, the error is undefined index.
Ok so I have a html file that has one text box with name 'number' and a one submit button. The form posts the value in text box to a php file "print.php".
print.php simply prints the number that was entered in the text box. When I run this in browser, it works correctly. 
We can also run php.exe sepreately from commandline. I read about it [here]("http://php.net/manual/en/features.commandline.php"). For example, I can type "php.exe print.php" in command prompt and it will displays all the errors. But the program does not know that I already have text box with name 'number'in a html file. How to do this ?

---

### Post by SteveHillier on 2010-01-13
I am no expert in this but I would guess this.
When you are running the script from the html file then the variable is getting passed from one routine to the other.  If you are compiling the print.php file without it knowing about the html file (the other side of the equation) then it will get confused - it cannot resolve the reference.
If I am wrong others will shoot me down.

ps I suspect you are trying to use php in a way it is not intended for.  The ability to compile php I guess is to enable libraries to be built for functions that have no need the have the value from forms to be passed to them

---

### Post by Hellkeepa on 2010-01-13
HELLo!

The reason you get the *notice* about an undefined index, is because you have not POSTed any data to the script. Thus there is no content in the "$_POST" array, yet you have not tested for this and is assuming there is.

Running the scripts via the PHP-CLI execuable is not the same as running them via the PHP-CGI (or Apache module). And the "compiling" your editor does, well.. Let's put it like this: I wouldn't depend on, nor use, it. And I write PHP code for a living.

Happy codin'!

---

### Post by Unlimited Bit on 2010-01-14
Just curious, why do you need to compile it ? :-s

---

### Post by mikejonesey on 2010-01-14
1. php does not compile
2. just add the following code around:

```
if($_SERVER['REQUEST_METHOD']=='POST')
{
...
}
```

---

### Post by Unlimited Bit on 2010-01-14
> **mikejonesey said:**
> 1. php does not compile
2. just add the following code around:

```
if($_SERVER['REQUEST_METHOD']=='POST')
{
...
}
```

Ask Google - there are a few PHP compilers / standalone executable generators.

---

