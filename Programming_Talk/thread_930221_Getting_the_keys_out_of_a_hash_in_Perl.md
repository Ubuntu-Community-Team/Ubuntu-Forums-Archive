---
title: "Getting the keys out of a hash in Perl"
date: 2008-09-25
forum: Programming Talk
---

### Post by YourSurrogateGod on 2008-09-25
```
%days_in_month = ( "July" => 31, "August" => 31, "Septemeber" => 30 );

print "The number of days in September: $days_in_month(September).\n";
$days_in_month{"September"} = 234235125;

print "The other number of days in September: $days_in_month{September}.\n";

@month_list = keys %days_in_summer;

print "Keys in days_in_month: $#month_list.\n";
print $month_list[1];
```

Just started learning Perl.

The problem is in the second last-line. I have no idea how you would get the whole list of keys from that hash. The second last print gives me "Keys in days_in_month: -1.

:/

---

### Post by myrtle1908 on 2008-09-25
You got alot of problems there buddy :)

Firstly always:

```
use strict;
use warnings;
```

These will help you to identify problems.

Secondly, you have spelled 'Septemeber' wrong in your hash declaration.

Thirdly, there is no hash named %days_in_summer.

Try this code:

```
use strict;
use warnings;

my %days_in_month = ( "July" => 31, "August" => 31, "September" => 30 );

print "The number of days in September: $days_in_month{September}.\n";

$days_in_month{September} = 234235125;

print "The other number of days in September: $days_in_month{September}.\n";

my @month_list = keys %days_in_month;

print "Keys in days_in_month: ", ($#month_list+1), "\n";

print $month_list[1];
```

---

### Post by ghostdog74 on 2008-09-25
always look for the docs first
```

perldoc -q hash

```

---

### Post by YourSurrogateGod on 2008-09-26
> **myrtle1908 said:**
> You got alot of problems there buddy :)

Firstly always:

```
use strict;
use warnings;
```

These will help you to identify problems.

Secondly, you have spelled 'Septemeber' wrong in your hash declaration.

Thirdly, there is no hash named %days_in_summer.

Try this code:

```
use strict;
use warnings;

my %days_in_month = ( "July" => 31, "August" => 31, "September" => 30 );

print "The number of days in September: $days_in_month{September}.\n";

$days_in_month{September} = 234235125;

print "The other number of days in September: $days_in_month{September}.\n";

my @month_list = keys %days_in_month;

print "Keys in days_in_month: ", ($#month_list+1), "\n";

print $month_list[1];
```

Cool thanks. Yeh, doing this pretty late doesn't help either :) .

---

### Post by YourSurrogateGod on 2008-09-26
> **ghostdog74 said:**
> always look for the docs first
```

perldoc -q hash

```

Oh so that's how you get to the docs. Thanks.

---

