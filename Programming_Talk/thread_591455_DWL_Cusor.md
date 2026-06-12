---
title: "DWL Cusor"
date: 2007-10-25
forum: Programming Talk
---

### Post by 008325 on 2007-10-25
i am doing a sql cursor , however , the if else question seems not working , no matter i type correrct value , it still can not rin the insert statement 

Please Help me 

Gordon


```

FETCH NEXT FROM @MyVariable
INTO @AbsEntry,@ItemCode,@Dscription,@RelQtty

	WHILE (@@FETCH_STATUS = 0) 
	BEGIN
		select @Code = ItemCode from @R1 where ItemCode = @ItemCode

		if (@code = 'A00001')
			insert into @R1 values(@AbsEntry,@ItemCode,@Code,@RelQtty)
					

	FETCH NEXT FROM @MyVariable
	INTO @AbsEntry,@ItemCode,@Dscription,@RelQtty
	End

select * from @R1
```

---

