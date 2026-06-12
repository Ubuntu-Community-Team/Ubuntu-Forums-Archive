---
title: "How to read txt or csv file using javascript?"
date: 2010-04-18
forum: Programming Talk
---

### Post by plusnplus on 2010-04-18
Hi..,
How to read txt or csv file using javascript?
the purpose is the collect some information from certain field/ coloum.
So it is important i can control, which coloum i want to get the value.

I try to google it, but I do not know how to modify it to able me to control which coloum i want to get the value.

The script will run inside html file.

Thanks for any help.

---

### Post by trent.josephsen on 2010-04-19
Javascript is not a good language for this sort of thing.  I'm not saying it can't be done, but I doubt you really want to do it.  It sounds like you are trying to do something on the client side that would be better performed on the server side, e.g. with a CGI script.  More information about the problem would help us to help you solve it better.

---

### Post by januzi on 2010-04-19
You can use javascript, but only if this is an ajax application. For example (jQuery):
```

<script type="text/javascript">
function read_csv() {
$.ajax({
   type: "GET",
   url: "script.php",
   data: [[data]],
   success: function(msg){
     alert( "Data from cvs: " + msg );
   }
 });}

```
Script.php reads specified file and prints formated text. That text goes as "msg" to the success function. Inside of that function You can alert, insert into div/span/p, etc. 
As for [[data]], You may need to write something like 
```

data: "columns="+x+","+y+","+z,

``` 
where x,y,z are selected columns (eg. 0,3,4)

---

