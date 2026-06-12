---
title: "Quick Perl Question"
date: 2009-11-11
forum: Programming Talk
---

### Post by MiniStephan on 2009-11-11
I'm starting to learn OOP Perl, and I came across this line of code when learning methods:

```
    sub name {
        my $self = shift;
        if (@_) { $self->{NAME} = shift }
        return $self->{NAME};
    }
```

What's the  if (@_) line used for?

---

### Post by myrtle1908 on 2009-11-11
> **MiniStephan said:**
> I'm starting to learn OOP Perl, and I came across this line of code when learning methods:

```
    sub name {
        my $self = shift;
        if (@_) { $self->{NAME} = shift }
        return $self->{NAME};
    }
```

What's the  if (@_) line used for?

It's checking if parameters were passed to the subroutine.  In this case, if there are parameters, it is shifting off the parameter list and setting NAME.

---

### Post by MiniStephan on 2009-11-11
Oh yeah, that helps, thanks.  I really should have seen that >.<

---

