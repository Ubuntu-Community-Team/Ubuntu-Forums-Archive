---
title: "Converting Julian Day to Gregorian MySQL"
date: 2010-07-28
forum: Programming Talk
---

### Post by Christian Christiansen on 2010-07-28
Hi,

I am trying to convert some functions from oracle, ms sql and db2 to mysql and I have reached a dead end. I need a function to convert Julian day to the Gregorian calender so 2455406 will be outputted as 2010-07-28 or 20100728.

Here is the code from the microsoft sql function:
```
drop function jdate2date

GO



CREATE FUNCTION jdate2date

(

	@indate int

)

RETURNS datetime

AS

BEGIN

	DECLARE @gregorian_date datetime

	

	if @indate > 0 

           SET @gregorian_date = cast((@indate-2415021) as datetime)

        else SET @gregorian_date = NULL

        

RETURN @gregorian_date

END

GO
```

I can post the code from db2 and oracle as well if necessary.
Thanks in advance.

---

### Post by Christian Christiansen on 2010-07-28
Okay if its going to be any help at all, I will now also include the other code as well.

db2:
```
CREATE FUNCTION JDATE2DATE(JDATE INTEGER)

    RETURNS TIMESTAMP

    LANGUAGE SQL

    CONTAINS SQL

    NO EXTERNAL ACTION

    NOT DETERMINISTIC

    RETURN (CASE JDATE

        WHEN 0 THEN NULL

        ELSE TIMESTAMP_ISO(DATE(JDATE-1721425)) 

        END);
```

oracle:
```
FUNCTION jdate2date(jdate number) return timestamp

is 

datetime timestamp;

begin

  begin

    if jdate = 0 then datetime := null;

    else

      datetime := to_timestamp(to_char(to_date(jdate,'J')),'DD-MON-RR');

    end if;

  exception when others then

    datetime := null;

  end;
```

Any help will be welcomed because I can't find documentation on this anywhere, and I have no idea how I can solve this problem.

---

