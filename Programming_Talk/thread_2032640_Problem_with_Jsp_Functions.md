---
title: "Problem with Jsp Functions"
date: 2012-07-24
forum: Programming Talk
---

### Post by DiegoTc on 2012-07-24
Hi
I am starting with JSP.
I would like to know why this doesn't work?

```

<%String msg="Hola"; %>
<%! public void getMsg()
{
 out.print(msg);
}%>	

```

This fragmement of code doesn't work?
The errors that appear are out cannot be resolved and msg cannot be resolved.

Any idea?

---

### Post by PaulM1985 on 2012-07-24
Just a guess but do you not want:
```

System.out.print(msg);

```
?

as for msg.. that is in a different set of JSP tags to the function.  I am not 100% familiar with JSP, but, guessing again, does Java think that the function and the variable are in different scopes?

Would
```

<%String msg="Hola";
public void getMsg()
{
 System.out.print(msg);
}%>

```
work?

Paul

---

### Post by greenpeace on 2012-07-25
> **PaulM1985 said:**
> ```

 System.out.print(msg);

```

I think the print function should be:

```
System.out.println( msg );
```

at least, that is what I have used... :)

---

### Post by PaulM1985 on 2012-07-25
> **greenpeace said:**
> I think the print function should be:

```
System.out.println( "msg" );
```

at least, that is what I have used... :)

I was assuming the OP wanted to print out the msg variable, which was the string "Hola".

---

### Post by greenpeace on 2012-07-25
> **PaulM1985 said:**
> I was assuming the OP wanted to print out the msg variable, which was the string "Hola".

Sorry you're right, no idea how those quote got in there!  Edited for clarity.

My point was that the command being "println", not "print".

---

