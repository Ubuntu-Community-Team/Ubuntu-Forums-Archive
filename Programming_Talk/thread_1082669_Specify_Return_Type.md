---
title: "Specify Return Type?"
date: 2009-02-28
forum: Programming Talk
---

### Post by Nullack on 2009-02-28
Im a beginner at C.

Since I added -Wall to my compiles, gcc is spitting out:

warning: return type defaults to ‘int’

Ive tried to search around the net and I understand that I need to specify my return type as an integer. My code is:

return 0;

I cant find any code samples and Im confused as to how to actually specify the return type as an int.

Sorry if this is a basic question  :)

---

### Post by leewebb on 2009-02-28
Posting your code would help to identify the correct reason, but it's most likely that you haven't specified a return type for main(). I.e., perhaps you have:


[FONT="Courier New"]main() 
{
  return 0;
}[/FONT]

when it should be:

[FONT="Courier New"]int main()
{
  return 0;
}[/FONT]

---

### Post by Nullack on 2009-02-28
Thanks

---

### Post by nvteighen on 2009-02-28
Heck... what book/tutorial are you using? It is either outdated or a really bad one.

---

### Post by Ferrat on 2009-02-28
could be he's using more than one and one of them is using void main

---

### Post by shadow_code on 2009-02-28
Easy mistake to make if your used to high level languages that don't require return types.

---

### Post by jimi_hendrix on 2009-02-28
> **shadow_code said:**
> Easy mistake to make if your used to high level languages that don't require return types.

*stares at most (all?) duck-typed languages*

---

### Post by nvteighen on 2009-03-01
> **shadow_code said:**
> Easy mistake to make if your used to high level languages that don't require return types.
What?

No, I don't think that's the issue here. OP was asking for a syntax issue, not the semantical one...

---

### Post by shadow_code on 2009-03-01
> **nvteighen said:**
> What?

No, I don't think that's the issue here. OP was asking for a syntax issue, not the semantical one...

Doesn't my post apply to both? ;)

---

### Post by nvteighen on 2009-03-01
> **shadow_code said:**
> Doesn't my post apply to both? ;)
I think not. I mean: I don't see the relationship between being used to duck-typing and this mistake. It can just be misinformation from the OP, with no needed relation between both phenomena.

---

### Post by shadow_code on 2009-03-01
> **nvteighen said:**
> I think not. I mean: I don't see the relationship between being used to duck-typing and this mistake. It can just be misinformation from the OP, with no needed relation between both phenomena.

Are, but if you're used to duck typing, you wouldn't think of specifying the return type in the function definition. I think it's unlikely that the OP's source material wouldn't specify a return type, so he may have just overlooked it!

This argument is so pointless :P

---

### Post by nvteighen on 2009-03-01
> **shadow_code said:**
> 
This argument is so pointless :P

Like a lot of the arguments in the PT :P

---

