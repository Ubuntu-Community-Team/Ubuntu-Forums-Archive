---
title: "[SOLVED] SQL: &amp;quot;Case&amp;quot; Expression"
date: 2008-10-04
forum: Programming Talk
---

### Post by balagosa on 2008-10-04
Hi, It is me again. Still having problems over the Same Project (Java Server Pages)

I have this Stored Procedure that receives two Parameters which are the order type, and order Key:
```
CREATE DEFINER=`root`@`localhost` PROCEDURE `spReportPos`(pOrder varchar(50), pKey varchar(50))
BEGIN
if(pOrder = 'desc') then
	select positionName,department from positions order by
	case pKey
	when pKey='department' then department
	when pKey='positionName' then positionName
	else salary
	end
	desc;
else
	select positionName,department from positions order by
	case pKey
	when pKey='department' then department
	when pKey='positionName' then positionName
	else salary
	end
	asc;
end if;
END
```

Then I have this table that only has two elements in it:
[b]
positionName             [COLOR="White"]asd asdasdasdassdasdasdasdasd[/COLOR]      department
A       [COLOR="White"]asd asdasdasdasdasdasdasdasdasdasdasdasd[/COLOR]                      DeptA
Z                       [COLOR="White"]asd asdasdasdasdasdasdasdasdasdasdasdasd[/COLOR]       DeptZ
[/b]

So I test out my Stored Procedure with this line: **CALL `HRMIS`.`spReportPos`('asc','department')**

The result should be ```
**First:DeptA** and **Second:DeptZ**
```

:confused:
**But guess what, it is the other way around.** I cheated the program and just inverted the order to get the **correct ResultSet**. So can anyone explain to me where I did go wrong?

---

### Post by balagosa on 2008-10-04
I already found out why it was wrong...
```

if(pOrder = 'desc') then
	select positionName,department from positions order by
	case **pKey**
	when pKey='department' then department
	when pKey='positionName' then positionName
	else salary
	end
	desc;
else
	select positionName,department from positions order by
	case **pKey**
	when pKey='department' then department
	when pKey='positionName' then positionName
	else salary
	end
	asc;
end if;

```
**I removed the pKey so it is**

```

select positionName,department from positions order by
	case
	when pKey='department' then department
	when pKey='positionName' then positionName
	else salary
	end

```

---

