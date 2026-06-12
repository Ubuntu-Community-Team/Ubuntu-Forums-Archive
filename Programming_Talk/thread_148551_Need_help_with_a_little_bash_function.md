---
title: "Need help with a little bash function"
date: 2006-03-22
forum: Programming Talk
---

### Post by el3ktro on 2006-03-22
Hello, I can't find a solution in any bash-howtos, so I hope you can help me. I have a little bash function:

```

function dosomething {
...
...
}

```

Then later on, I want to continue only if the function has been run successfully:

```

if dosomething; then
...
...
fi

```

This works good so far. Now I need the function to have an parameter. The script is called with an username as $1, and I have to hand this parameter over to the function, so I have to call the function like this:

```

dosomething $1

```

Which will hand over the first script parameter to the function, right? But, how do I do this within the "if" statement? This doesn't work:

```

if dosomething $1; then

```

I've tried several things, but nothing works. How do I do that?

Tom

---

### Post by kabus on 2006-03-22
I'm not sure why it doesn't work, but maybe you could just replace it with :

```
dosomething $1
if [ $? -eq 0 ]; then
dosomethingelse
fi
```

---

### Post by el3ktro on 2006-03-22
Oh damn shame on me, I'm so stupid. Well I actually had

if dosomething && dosomethingdifferent; then

and I only tried it with the first one, not the second one, so these error msgs tricked me.

if dosomething $1 && dosomethingdifferent $1; then

actually works! Again, shame on me :-(

Thanks anyway for your tip!

Tom

---

