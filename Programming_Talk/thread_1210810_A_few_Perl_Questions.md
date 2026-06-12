---
title: "A few Perl Questions"
date: 2009-07-11
forum: Programming Talk
---

### Post by dellwood on 2009-07-11
Hi, 

I have two Perl questions I just can't seem to find an answer for:

1) How can I check if the directories in the @INC ('path') array contain certain [EDIT] items/directories?  For instance, if the directory 'perl' is located in any of the paths from @INC

2) Is there an easy way to turn on/off the 'die' function?  I know this may sound a bit confusing, so lets say in the following example: 

```

sub routine
{
    my( $arg1, $arg2, $arg3, $die_switch ) = @_;

    if( $die_switch = 1 )
    {
        #keep all die statements in place
    }
    elsif( $die_switch = 0 )
    {
        #ignore all die statements
    }
    else
    {
       ...
    }
    ...
}

```

How could this toggling of the 'die' command be achieved?

All help is welcome and appreciated :).

-Josh

---

### Post by slavik on 2009-07-11
1. search for it ...
```

for my $dir (@INC) {
  print $dir."\n" if ($dir =~ /somedir/);
}

```

2. create a wrapper
```

our $dead_die = 0; #set to false

sub die_wrapper {
  if ($dead_die) {
    die @_;
  }
}

```

Make sense?

---

### Post by dellwood on 2009-07-12
I get the first one (thanks), but I am having trouble with the second one: 

1) Set the toggle variable --got it

2) make the sub routine --ok

3) check what the variable is set to --yep

4) Die and print the arguments list -- ? (This is where I'm stuck).

Mabye I didn't elaborate enough on what I meant, and if so that sorry that's my fault and (just in case) I'll try to do so now.  If I have 4 'print $var' statements followed by 'or die' statements, how can I make a simple on/off variable to make the interpreter see or ignore the die statements. 

If you already knew what I meant sorry, mabye I'm just missing something :-k :).

Sorry for the inconvience (and thanks again).

-Josh

---

### Post by unutbu on 2009-07-12
I think slavik is suggesting that you change
```

print "$var" or die("Alas, poor Yorick");
```

to 
```

print "$var" or die_wrapper("Alas, poor Yorick");
```

---

### Post by dellwood on 2009-07-12
Oh! #-o I fell slightly dumb right now :).

Thanks.

-Josh

---

### Post by slavik on 2009-07-12
> **unutbu said:**
> I think slavik is suggesting that you change
```

print "$var" or die("Alas, poor Yorick");
```

to 
```

print "$var" or die_wrapper("Alas, poor Yorick");
```
[quote=Heavy]Engineer is credit to team![/quote] :)

---

