---
title: "Need help with a Javascript function"
date: 2007-07-22
forum: Programming Talk
---

### Post by akudewan on 2007-07-22
Hi,

I'd written a simple program in C (one that converts a number into words), which I want to write in javascript now.
I have a recursive function called "putzero()" which adds zeros to the beginning of a number to make it divisible by 3. The function seems to be working, but when it returns a value, my number becomes "undefined".

Here's the stripped down code:
```

<html>
<head>
<script type = "text/javascript">

function putzero(num)
{
   var len = num.length
   if((len%3) == 0)
      {
      document.write(num);
      return(num);
      }
   else
   {
      num = '0' + num;
      putzero(num);
   }

}

   var number = prompt("Enter Number");
   document.write(typeof(number),"<br>")
   number = putzero(number);
   document.write("<br>",number);
   
</script>

<body>

</body>

</html>

```

When I enter 1234, my output is:
```

string
001234
undefined

```

Can anyone help me with this?

Thanks.

---

### Post by winch on 2007-07-22
putzero() only returns a value if the length is divisible by 3. If the length isn't divisible by three no value is returned and so you get undefined.

Since the number of required iterations can easily be calculated why use recursion?

```

<html>
<head></head>
<body>
<script type = "text/javascript">

function putzero(num)
{
   var len = num.length
   count = len % 3;
   if (count != 0)
   {
      for (i = 3; i > count; i--)
      {
           num = 0 + num;
      }
   }
   return num;
}

   var number = prompt("Enter Number");
   document.write(typeof(number),"<br>")
   number = putzero(number);
   document.write("<br>", number);
   document.write("<br>", number.length);
   
</script>
</body>
</html>

```

---

### Post by nitro_n2o on 2007-07-22
I've tried your script it works fine with so many other values also :) 
wht browser r u using?

p.s: you may want to close the <head> tag, but this shouldn't be a problem

---

### Post by akudewan on 2007-07-22
@winch:
In my C program, the function argument was character pointer. Since I can't have a pointer in Javascript, the function was creating a new variable everytime the function called itself, and when it went back, my return value became undefined, is that correct ?

Thanks for the help, I'll use the loop instead of recursion.

@nitro_n2o: I'm using firefox, but I'll test on Opera and IE later.

Thanks again.

---

