---
title: "Awk help please!"
date: 2015-07-02
forum: Programming Talk
---

### Post by robertsclark on 2015-07-02
I am trying to fix a CSV data file that has some data wrongly set.  The specification that I have been given is:

For all type 24 records
Rule 1:
Where a Postcode and Posttown exist and the status is not 3, the Postal Address should be ‘Y’.  
 
Rule 2
Where a Postcode exists with no Posttown and the status is not 3, the Postal Address should be ‘P’ and not ‘N’
 
Rule 3
Where a Postcode exist with or without a Posttown and the logical Status is 3, the Postal Address should be ‘A’ and not ‘N’

All other records should be copied without being touched.

Record type is field 1
Postcode is field 25
Posttown is field 26
Status is field 7 and
Postal Address is field 24

I though that awk would be a suitable tool to do this (I am actually using gawk under Windows 8).  I have been trying to code the fix for the first rule:

BEGIN {
FS = ","
OFS = ","
};

fix = "";
if ( $1 == 24 ) {
    if ($25 != "" && $26 != "" && $7 != 3 && $24 != "Y" {
        $24 = "Y"; fix = "FIXED!"; };
    print $0 fix;
};
}

Unfortunately this isn't working as it is marking nearly all records as fixed instead of about three or four.

Anyone able to offer any advice?  Data file attached - the Type 24 records are at the end of the file

Regards

Robert

---

### Post by tgalati4 on 2015-07-02
I'm getting syntax errors.

A few comments.  The data that you attached looks like real mailing list data, which is probably not a good idea to post on an open forum.
You want to use ```
 tags when posting code snippets.

Now I have to figure out why I'm getting syntax errors:

> tgalati4@Mint17 ~/Downloads $ awk -f address_fixer.awk type_24_data.txt 
awk: address_fixer.awk:7: if ( $1 == 24 ) {
awk: address_fixer.awk:7: ^ syntax error
awk: address_fixer.awk:8: if ($25 != "" && $26 != "" && $7 != 3 && $24 != "Y" {$24 = "Y"; fix = "FIXED!"; };
awk: address_fixer.awk:8:                                                     ^ syntax error
awk: address_fixer.awk:11: }
awk: address_fixer.awk:11: ^ syntax error


My awk skills are weak today. Still getting errors with this script:

[code]BEGIN {FS = ",";OFS = ","};
fix = "";
if ( $1 == 24 ) {if ($25 != "" && $26 != "" && $7 != 3 && $24 != "Y" ) $24 = "Y"; fix = "FIXED!" };
print $0 fix;
};
};
END {}

```

> tgalati4@Mint17 ~/Downloads $ awk -f address_fixer.awk type_24_data.txt 
awk: address_fixer.awk:3: if ( $1 == 24 ) {if ($25 != "" && $26 != "" && $7 != 3 && $24 != "Y" ) $24 = "Y"; fix = "FIXED!" };
awk: address_fixer.awk:3: ^ syntax error
awk: address_fixer.awk:4: print $0 fix;
awk: address_fixer.awk:4: ^ syntax error
awk: address_fixer.awk:5: };
awk: address_fixer.awk:5: ^ syntax error
awk: address_fixer.awk:6: each rule must have a pattern or an action part
awk: address_fixer.awk:6: };
awk: address_fixer.awk:6: ^ syntax error
awk: address_fixer.awk:7: each rule must have a pattern or an action part


This might work:

```
BEGIN {FS = ",";OFS = ","};
{
fix = "";
if ( $1 == 24 ) {if ($25 != "" && $26 != "" && $7 != 3 && $24 != "Y" ) $24 = "Y"; fix = "FIXED!" };
print $0 fix;
};

```

---

### Post by steeldriver on 2015-07-02
I don't think your [FONT=courier new]$26 != ""[/FONT] expressions are doing what you think they are: awk is treating these as tests for whether the field is non-*empty*, whereas you probably want to test for absence of literal double quotes? Compare

```

$ echo -e 'a,b,c\na,"",c' | awk -F, '$2 != ""'
a,b,c
a,"",c

```
versus
```

$ echo -e 'a,b,c\na,"",c' | awk -F, '$2 != "\"\""'
a,b,c

```

---

### Post by SeijiSensei on 2015-07-02
Personally the rules you report are sufficiently complex that I would do all these tasks in a spreadsheet program where you can write IF() statements and the like.  Awk seems too primitive to me for a task like this.

I use awk and sed all the time, but I wouldn't choose them for this task.

---

### Post by tgalati4 on 2015-07-02
I agree, for the dataset presented a spreadsheet would work well.  But for a big data application, then *awk* will do the trick, you just need to pay attention to the syntax and the logic.  Scripting languages are sensitive to these errors.

---

### Post by robertsclark on 2015-07-03
@steeldriver Thanks - by escaping the quote symbol I have managed to get this to work.

@seijisensi, @tgalatia4 - I did the prototyping in Excel to make sure that the rules specification worked, but now that I want to automate it (and include it in a regular batch job), I think it makes more sense to use a tool like awk.

My final version

BEGIN {
FS = ","
OFS = ","
};

{
if ($1 == 24) {
    if ($25 != "\"\"" && $26 != "\"\"" && $7 != 3 && $24 !~ ""Y")
        {$24 = "Y"};
    if ($25 != "\"\"" && $26 == "\"\"" && $7 != 3 && $24 !~ "P")
        {$24 = "P"};
    if ($25 != "\"\"" && $7 -- 3 && $24 !~ "A")
        {$24 = "A"};
};
print $0;
}

---

