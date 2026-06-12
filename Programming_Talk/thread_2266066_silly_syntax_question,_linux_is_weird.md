---
title: "silly syntax question, linux is weird"
date: 2015-02-19
forum: Programming Talk
---

### Post by pgib8 on 2015-02-19
I've been programming for a long time both in C and C++, but some of that code I see in Linux doesn't make sense to me and I would like to understand it. For example:

```
[COLOR=#000000]struct platform_driver {[/COLOR]	int (*probe)(struct platform_device *);
	int (*remove)(struct platform_device *);
	void (*shutdown)(struct platform_device *);
	int (*suspend)(struct platform_device *, pm_message_t state);
	int (*suspend_late)(struct platform_device *, pm_message_t state);
	int (*resume_early)(struct platform_device *);
	int (*resume)(struct platform_device *);
	struct device_driver driver; [COLOR=#000000]};
[/COLOR]
```

Let's just take the first one:
int (*probe)(struct platform_device *);

What the heck does that mean? (lol)
Is this C or C++?

---

### Post by steeldriver on 2015-02-19
My C is rusty, but they're pointers to functions I think i.e. in

```

int (*probe)(struct platform_device *)

```

'probe' is a *pointer to a function* that takes a pointer to a struct platform_device, and returns an int

See [http://www.cprogramming.com/tutorial/function-pointers.html](http://www.cprogramming.com/tutorial/function-pointers.html) for example.

---

### Post by pgib8 on 2015-02-19
ok, so it's a pointer to a function, like a callback function. I read the link you gave me and now I have a pretty good understanding. I successfully compiled the following:
```


static struct platform_device lol;


static int testf(struct platform_device *);
void bla(void);






void bla(void) {
  struct platform_device lol2;
  int x2;


  lol.probe = testf;




  x2 = lol.probe(&lol2);              //these two are the same thing
  x2 = testf(&lol2);


}


static int testf(struct platform_device *x) {


  return 0;
}



```

Any code that is outside of my code, and that has access to the platform_device structure that I define, will be able to call the probe function, which will point to my function (in this case testf).

---

### Post by spjackson on 2015-02-20
Could you please explain how any of this makes Linux (rather than C) "weird": I don't follow. Thanks.

---

### Post by dwhitney67 on 2015-02-21
> **pgib8 said:**
> I've been programming for a long time both in C and C++, ....

Not long enough, I suppose.

> **pgib8 said:**
> 
```
[COLOR=#000000]struct platform_driver {[/COLOR]	int (*probe)(struct platform_device *);
	int (*remove)(struct platform_device *);
	void (*shutdown)(struct platform_device *);
	int (*suspend)(struct platform_device *, pm_message_t state);
	int (*suspend_late)(struct platform_device *, pm_message_t state);
	int (*resume_early)(struct platform_device *);
	int (*resume)(struct platform_device *);
	struct device_driver driver; [COLOR=#000000]};
[/COLOR]
```

...

Is this C or C++?

The code above could be either C or C++, but judging by the last declaration in the platform_driver struct (and other declarations where the keyword 'struct' is used), I'd say this is C.

P.S.  In your lengthy studies of C and C++, surely you know that in C++, there's no difference between a struct and a class, other than in the latter, unless specifically indicated, all declarations are considered private.  For example, these are equivalent in C++:

```

struct Foo
{
    int pub_value;

private:
    int priv_value;
};

class Foo
{
    int priv_value;

public:
    int pub_value;
};

```

---

### Post by ofnuts on 2015-02-21
> **dwhitney67 said:**
> 
The code above could be either C or C++, but judging by the last declaration in the platform_driver struct (and other declarations where the keyword 'struct' is used), I'd say this is C.

Also, in C++ you wouldn't be using a struct of pointer to functions... this is exactly what objects (with virtual methods) are all about :)

---

### Post by dwhitney67 on 2015-02-21
> **ofnuts said:**
> Also, in C++ you wouldn't be using a struct of pointer to functions... this is exactly what objects (with virtual methods) are all about :)

Yeah.  I could not have said it better in farfugnuggenlugen language.

---

