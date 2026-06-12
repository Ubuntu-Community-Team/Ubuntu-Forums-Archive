---
title: "Postgresql issue."
date: 2008-11-07
forum: Programming Talk
---

### Post by fredscripts on 2008-11-07
Hi!!

I have a table with an field called dni, say:

```
CREATE TEMP TABLE  User (
  user_id serial,
  dni dni_domain,

  CONSTRAINT const_user_pk PRIMARY KEY(user_id)
);
```

Where dni_domain is:

```
CREATE DOMAIN dni_domain char(9) CHECK (value ~* '[0-9]{8}[a-z]{1}');
```

Dni is similar to an identification number. Examples of DNI are: 12345678A , 11111111B, 44444444C,...

So say I want to fill the table with a lot of records in order to check if would be useful to put an index on DNI (of course it would, but I need to demonstrate it in terms of run time).

So I'm trying to make a function that inserts a lot of records (especified by parameters of the funcion) into User, having each user entry a different DNI.:

```

CREATE OR REPLACE FUNCTION loadtable_user(integer) RETURNS integer AS '

DECLARE
i integer;
dni_u char(9);

BEGIN
        -- $1 is the parameter of the function (max number of inserts)
	FOR i IN 1..$1
	LOOP  
		dni_u = cast(i as char(8)) || ''A'';
		
		INSERT INTO User(dni) VALUES(dni_u);
			
	END LOOP;

	RETURN 1;
END;

'LANGUAGE  'plpgsql';

SELECT loadtable_user(10000);
```

So I want this function to be inserting users with different DNI, in the form:

00000001A
00000002A
00000003A
00000004A
00000005A
...
99999999A

All right, so it seems I'm not doing correct the casting:
```
dni_u = cast(i as char(8)) || ''A'';
```

Because the CHECK error appears, meaning that the dni_u doesn't pass the dni_domain constraints.

Anyone has an idea of how could I achieve this behaviour?

*IMPORTANT*: I'm running Postgresql 7.4.18 (I know is quite old, but wasn't my choice). It has really annoying bugs respect to >8 version, but I hope with your help I'll be able to code that simple function.

Thanks so much!!!

---

### Post by slavik on 2008-11-07
your check does [a-z]{1} ... are you sure it is not case sensitive?
also, doesn't || in Python mean what it means in most other languages (logical OR) ...
I think you want something like: dni_u = str(cast(i as char(8))) + "A"

Please keep in mind that I am not a Python expert my any means and I don't even use it :P

---

### Post by fredscripts on 2008-11-08
Thanks for answering!!

Just want to remain you that this isn't Pyhton. It's the procedural language "plpgsql". So obbiously it has completely different syntax.

The regex of dni_domain is case isensitive (using ~*).

---

