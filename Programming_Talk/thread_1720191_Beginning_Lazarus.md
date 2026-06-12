---
title: "Beginning Lazarus"
date: 2011-04-02
forum: Programming Talk
---

### Post by Learning Linux 2011 on 2011-04-02
Hi,

I am new to Lazarus, and it seems somewhat overwhelming.  Can anyone assist me with the basics?  

If I have the following Pascal code:

```

Program Square;

{This program reads a number and displays its square.}

var
   n : integer;

begin
   Writeln ('Enter the number to be squared');
   Readln (n);
   Writeln ('The square of ', n, ' is ', Sqr(n));
end.

```
Can anyone explain how to make a "form" with this in Lazarus?  

For example, (if it isn't too difficult to explain), how would I read an integer in a form, square it using the above code, and then print out the result either in the same form or another form?

I would appreciate any help you can give.

---

### Post by Balf on 2011-04-03
I'm new to it as well!  I found this helped.

[http://wiki.lazarus.freepascal.org/Lazarus_Tutorial](http://wiki.lazarus.freepascal.org/Lazarus_Tutorial)

---

### Post by raydeen on 2011-04-04
You would start with an empty form and perhaps place two text edit boxes and a button on it. Then double click the button to bring up it's subprocess code. It should look like:

```

procedure TForm1.Button1Click(Sender: TObject);
begin

end;

```

You'd then put your code in that would take the value of TEdit1.Text, store it in a variable, square the variable and then have TEdit2.Text = the new value of that variable.

---

