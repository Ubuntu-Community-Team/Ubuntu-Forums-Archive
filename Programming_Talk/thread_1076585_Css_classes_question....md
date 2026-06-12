---
title: "Css classes question..."
date: 2009-02-21
forum: Programming Talk
---

### Post by hockey97 on 2009-02-21
Hi, I  need to make some modification to  someones code.


Currently they have all the classes set.


In   the tabs of the website. I need to make it  the font color different for just one  text.

The class already sets all fonts to one color.


Is there a way I can over ride the first text color set for the tabs?


I tried making the tab green with using <a class="2nd color"> Service tab</a>

The first color is set to blue. 

 but  I want to make changes to just this one tab. I just want to know if there is a way I can  just add some code to make just that tab to be a different color without  doing major changes.

Cause the font type and other definitions are set with these tabs and I don't want to change any that code I still want those setting to be applied to this one tab but just I don't want the default color to be set for this font.

here is the css code:
```
.tabs ul li a {
				height:34px;
				padding:19px 30px 0;
				display:inline-block;
				text-decoration:none;
				text-transform:uppercase;
				color:#6d96cd;
				font-size:1.5em;
				}

```


and here is the html code:




The class is called tabs but it  has css code for the tags inside the div. Like tags ul  and li and a 

the a tags are the ones that Shows the Texts.

Can I override the default tag a settings by  adding  a.font_color_2  

then just change the color to  green.  

I just want to change  one text  to a different color then the default  settings in css.

---

### Post by nvteighen on 2009-02-21
If you create a child class, whatever you modify in there will be overriden. a.font_color2 should work.

---

### Post by hockey97 on 2009-02-21
so if the css is like this :

```
.tabs  a.color_2{
 
                                height:34px;
				padding:19px 30px 0;
				display:inline-block;
				text-decoration:none;
				text-transform:uppercase;
				color:#(new color);
				font-size:1.5em;
                                }


```

if that is the case would I in the html code  just add <a class="color_2".

would that be how I would put the  a tag to overwrite the previous defualt settings color?

---

### Post by nvteighen on 2009-02-21
No, it's much simpler:

```

.tabs ul li a {
	height:34px;
	padding:19px 30px 0;
	display:inline-block;
	text-decoration:none;
	text-transform:uppercase;
	color:#6d96cd;
	font-size:1.5em;
}
```

And then:
```

a.color2 {
    color:#(new color);
}

```

That overrides whatever color you used for a, but keeps the rest. If you're familiar with Class Inheritance in some OOP languages, well, now you may understand why CSS also has "classes" :)

---

### Post by Peter76 on 2009-02-21
You could also give it an id ( something like greentab ) and aply the color style to that.

---

### Post by hockey97 on 2009-02-21
ok, I see kinda... just one more question.

Would I still have the tabs class still applying other settigs.

Cause I don't want to mess up the previous settings that set how others should look.

so when I make the new class it would be like  a.color_2{  }

not   .tabs a.color_2{  }

? 


They use a div and add the class tabs. This divs surrounds all the tabs.

So in the css code they set settings for within that div that would be default settings.

then they would have a setting for tags like  ul  li and  a 

so  I don't need to use   .tabs a.color_2{ }

I can just put a.color2( )


then in the html I just add a class for that a tag I want the font color to change.

I would just put something like <a class="color_2"  ... is that right?


ok well this is what I done to it so far.

```
 .tabs ul li a.color2 {
				color:#00CC66
			        }

```

---

### Post by nvteighen on 2009-02-21
You're right. You just use <a class="color2" ...>...</a> and what will happen is that first the **.tabs ul li a {}** specs will be applied and then, **a.color2 {}**, therefore overriding the color attribute, but keeping the others intact.

The id solution is also possible if it's just a single element which needs to override its class propierties.

---

### Post by hockey97 on 2009-02-21
OK never mind. Thanks for the help. I looked at the code and forgot to put a ; at the end of color.

---

### Post by slavik on 2009-02-21
I would not suggest doing that since the idea behind ids is that they are unique and you may start using them for the purpose that class exists for.

also, if you need to overwrite anything, you can do it in the tag itself.

---

### Post by nvteighen on 2009-02-22
> **slavik said:**
> 
also, if you need to overwrite anything, you can do it in the tag itself.

That's against the good practices :p

---

### Post by drubin on 2009-02-22
> **nvteighen said:**
> That's against the good practices :p

Since when? 

are you talking about giving  h1's overwridden styles?

ie
[PHP]
h1{
/*boo bar foo baz*/
}
b { 
font-color: green;
}
[/PHP]

---

### Post by nvteighen on 2009-02-22
Eh? No, I was referring to override styles at the HTML tags, which was what slavik seemed to imply in his post. Overriding styles in CSS is the best practice.

---

### Post by drubin on 2009-02-22
> **nvteighen said:**
> Eh? No, I was referring to override styles at the HTML tags, which was what slavik seemed to imply in his post. Overriding styles in CSS is the best practice.

O ye that is bad mkay :)

---

