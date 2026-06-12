---
title: "Ruby Tk"
date: 2008-02-21
forum: Programming Talk
---

### Post by toothyXdip on 2008-02-21
Ok ive just been messing around with ruby tk a little today and i have a question about a little thing. Im trying to just making it where there is a label (preferably a inputbox with read only text but i dont know how to do that yet) and theres a button and when you press the button it adds 1 to the number in the box or on the label. I tried doing that with this:

```

require 'tk'
def addnumber
	command @number =+ 1
end

buttonclicked = proc {addnumber}
@number = 1
hello = TkRoot.new do  
  title "Hello World"  
  # the min size of window  
  minsize(400,400)  
end  
TkLabel.new(hello) do 
	@number = 1
  text "#{@number}"
  foreground 'red'  
  pack { padx 15; pady 15; side 'left'}  
end
TkButton.new do  
  text "Add 1"  
  command addnumber
  pack('side'=>'left', 'padx'=>10, 'pady'=>10)  
end  
Tk.mainloop 

```

why isnt this working?

---

### Post by foo-bar on 2008-02-21
When you update the number attribute, you may have to update the text of the label as well (my assumption is that ruby will not automatically link any changes made to the variable to the label as well).

---

### Post by stevescripts on 2008-02-22
Well, being a long-time heavy user of tcl/tk - your post prompted me to install
Ruby on a couple of boxes and play with it.  (Nice language, BTW - gonna spend some
time tinkering with it)

Maybe ugly to a ruby hacker, but, this *works for me*:

```

require 'tk'

theNum = 1

def plus1(var)
 var = var + 1
end

hello = TkRoot.new do  
  title "Hello World"  
  # the min size of window  
  minsize(400,400)  
end  

lbl = TkLabel.new(hello) do 
  text theNum
  foreground 'red'  
  pack { padx 15; pady 15; side 'left'}  
end

btn = TkButton.new(hello) do  
  text "Add 1"  
  command proc { lbl.configure('text'=> theNum = plus1(theNum))}
  pack('side'=>'left', 'padx'=>10, 'pady'=>10)  
end  

Tk.mainloop

```

Basically, you just needed a callback to configure the label.

Hope you find this helpful.

Steve

---

### Post by stevescripts on 2008-02-25
A few days later, (and a few hours to tinker with Ruby and read up
a bit...)

Like I said, the solution I posted earlier *felt* like a hack...

This looks (for now, at least) better:
```

require 'tk'

theNum = 1

def plus1(var)
 var = var + 1
end

hello = TkRoot.new() { title "Hello World!" }

lbl = TkLabel.new(hello, "text"=>theNum, "foreground"=>"red", "width"=>13, "relief"=>"groove").grid("row"=>0, "column"=>0)

btn = TkButton.new(hello, "text"=>'Add 1' ).grid("row"=>0, "column"=>1)

btn.bind("ButtonRelease") { lbl.configure('text'=> theNum = plus1(theNum))}

hello['resizable'] = false, false

Tk.mainloop

```

Any ruby hackers, feel free to critique. ;)

Another update, perhaps, as I get a bit more comfortable
with Ruby syntax ...

Steve

---

### Post by stevescripts on 2008-02-28
One last update ...

I was reasonably sure, that RubyTk supported Tk's textvariable,
and that I could eliminate the bind callback in the previous script.

This doesn't feel like a hack anymore.

So, here it is:
```

#! /usr/bin/ruby

require 'tk'

def plus1(var)
 var = var + 1
end

$result = TkVariable.new(0)

hello = TkRoot.new() { title 'Hello World!' }

lbl = TkLabel.new(hello, 'textvariable'=> $result, 'foreground'=>'red', 'width'=>13).grid('row'=>0, 'column'=>0)

btn = TkButton.new(hello) {text'Add 1'; command {$result.value = plus1($result)}}.grid('row'=>0, 'column'=>1)

hello['resizable'] = false, false

Tk.mainloop

```

Again, any comments/critique from ruby coders appreciated.

Steve

---

