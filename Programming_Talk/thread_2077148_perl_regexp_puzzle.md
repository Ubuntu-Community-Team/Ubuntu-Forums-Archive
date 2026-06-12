---
title: "perl regexp puzzle"
date: 2012-10-27
forum: Programming Talk
---

### Post by paxxus on 2012-10-27
Hi, I'm really struggling with this.

This perl program successfully parses past the blank lines and comments:

```

$s = <<END;

// Hello

// World
xxx
END

$s =~ m,\G((//.*)?\s*)*,mgc;

print ">", $s, "<\n";
print ">", substr( $s, pos( $s ) ), "<\n";

```As expected it parses to the 'xxx' and the output is:

```

>
// Hello

// World
xxx
<
>xxx
<

```However, if I change the regexp to:

```

$s =~ m,\G(\s*|//.*)*,mgc;

```It only parses the first blank line :confused:

The non-functional regexp simply says that it should match zero or more sequences of white-space or line-comments, but it doesn't work for some reason, and I'd like to know why.

---

### Post by paxxus on 2012-10-30
I found that if I swap the OR operator like:

```

$s =~ m,\G(//.*|\s*)*,mgc;

```This it works. I can also just change * to +, like:

```

$s =~ m,\G(\s+|//.*)*,mgc;

```Still, it's not entirely clear to me what's going on.

---

### Post by ofnuts on 2012-10-30
> **paxxus said:**
> I found that if I swap the OR operator like:

```

$s =~ m,\G(//.*|\s*)*,mgc;

```This it works. I can also just change * to +, like:

```

$s =~ m,\G(\s+|//.*)*,mgc;

```Still, it's not entirely clear to me what's going on.
because "\s*" will always match... between any two character there are 0 or more spaces...you should be trying to match a line with only spaces (^\s*$) or  a lines with 0 or more leading spaces and the comments (^\s*//).

---

### Post by paxxus on 2012-10-31
Yes, I think I understand now. The | is not greedy, it just selects the first possibility which matches regardless that a later | "branch" also matches with a longer sequence.

---

