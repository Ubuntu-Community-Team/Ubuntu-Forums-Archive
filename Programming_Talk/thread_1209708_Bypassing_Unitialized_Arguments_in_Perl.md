---
title: "Bypassing Unitialized Arguments in Perl"
date: 2009-07-10
forum: Programming Talk
---

### Post by dellwood on 2009-07-10
Hi, 

In a perl subroutine, is there a way to bypass an argument in a subroutine, or ( the mote messy route ) ignoring uninitiated values at the end of an argument list?

So, for the first option, if I have the following code:

```

sub routine
{
    my ( $a, $b, $c ) = @_;
    if( $a = 'a' )
    {
        #do something
    }

    if( $b = 'b' )
    {
        #do something different
    }

    if( $c = 'c' )
    {
        #do something different from the first to
    }
}

routine('a', 'c');

```

how can it be made to bypass b all together?

Now, the other way, which seems a bit more realistic (but also more confusing).

```

sub routine
{
    my( $a, $b, $c ) = @_

    if( $a = 'a' )
    {
        #do what a would do
    }
    if( $a = 'b' )
    {
        #do what b would do
    }
    if( $a = 'c' )
    {
        #do what c would do
    }
    
    if( $b = 'a')
    {
        ...
    }
    ...
    if( $c = 'a')
    {
        ...
    }
    ...
}

routine('b', 'a');

```

This way lets any of the 3 arguments be any of the other three, but if I put the same input in as above, I get the first to values followed something along the lines of "unitilized value $c." 

Is there a way around this(besides turning off warnings)?

Thanks :)

-Josh

---

### Post by nvteighen on 2009-07-10
I would accept a hash (or maybe a hash reference) as unique parameter, so you refer to your "parameters" (actually the content in your hash) by their keys... Or if you just want one optional argument, you could test @_'s length...

Look at [http://www.perl.com/pub/a/2006/02/23/advanced_subroutines.html](http://www.perl.com/pub/a/2006/02/23/advanced_subroutines.html)

---

### Post by soltanis on 2009-07-10
There isn't a named arguments feature if that's what you're looking for, though passing a hash like above poster said will basically do this for you. You could also call the subroutine like:

```

routine('a', undef, 'c');

```

Although the usefulness of this scheme is pretty limited (not to mention that you'd need to be checking for undef arguments in the subroutine).

---

### Post by unutbu on 2009-07-10
```
sub routine {
    my ($args)=@_
}
```

is convenient but possibly evil. It obscures the subroutine's true call signature. 
In other words, you can't tell just by looking at the first few lines of the 
subroutine what arguments are expected, what's optional and what's mandatory. 

If you use this technique in a large project, you would be wise (wiser than I :)) 
to document all the possible ways the subroutine can be called thoroughly.

---

### Post by zakame on 2009-07-11
> **dellwood said:**
> Hi, 

In a perl subroutine, is there a way to bypass an argument in a subroutine, or ( the mote messy route ) ignoring uninitiated values at the end of an argument list?


As you put it, the argument list (@_) contains a positional list of arguments, so if you intend to ignore a parameter, you can just put in `undef' as the value, as in

```
call_my_agent( $lol, undef, $what );
```

> **dellwood said:**
> 
Now, the other way, which seems a bit more realistic (but also more confusing).

```

sub routine
{
    my( $a, $b, $c ) = @_

    if( $a = 'a' )
    {
        #do what a would do
    }
    if( $a = 'b' )
    {
        #do what b would do
    }
    if( $a = 'c' )
    {
        #do what c would do
    }
    
    if( $b = 'a')
    {
        ...
    }
    ...
    if( $c = 'a')
    {
        ...
    }
    ...
}

routine('b', 'a');

```

This way lets any of the 3 arguments be any of the other three, but if I put the same input in as above, I get the first to values followed something along the lines of "unitilized value $c." 

Is there a way around this(besides turning off warnings)?

Thanks :)

-Josh

You'll want to consider using a hash (or hash reference) as a parameter, like this:

```

sub your_function {
    my %args = @_;

    do_something( $args{a} )   if $args{a};
    do_another( $args{b} )     if $args{b};
    do_yet_another( $args{c} ) if $args{c};
}

# call it like this
your_function({ a => 1, b => 2, c => 3 });

# or this
your_function({
    a => 'lol',
    c => 'wut',
});

```

---

### Post by prkfriryce on 2009-07-11
> **soltanis said:**
> There isn't a named arguments feature if that's what you're looking for, though passing a hash like above poster said will basically do this for you. You could also call the subroutine like:

```

routine('a', undef, 'c');

```

Although the usefulness of this scheme is pretty limited (not to mention that you'd need to be checking for undef arguments in the subroutine).

ditto

---

