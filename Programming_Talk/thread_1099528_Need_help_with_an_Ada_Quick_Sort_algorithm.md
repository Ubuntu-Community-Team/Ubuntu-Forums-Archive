---
title: "Need help with an Ada Quick_Sort algorithm"
date: 2009-03-18
forum: Programming Talk
---

### Post by mcmillhj on 2009-03-18
Hey everyone, im working on a program that uses a quick sort algorithm to sort a relatively small array, size 14. I keep getting invalid prefix in selected component error. I was wondering if someone could tell me why.

Here's my code:
```

generic
	type Element_Type is private;
	type Array_Type is array (Positive range <>) of Element_Type;
	with function "<" (Left : in Element_Type; Right : in Element_Type)
							return Boolean;
	procedure Quick_Sort(Values : in out Array_Type);


```

```

    procedure Quick_Sort(Values : in out Array_Type) is
   
   -------------------------------------------------------------------------------------
       procedure Swap(Left : in out Element_Type; Right : in out Element_Type) is
      --Swaps hte values of two variables 
         Temp : Element_Type;
      begin 
         Temp := Left;
         Left := Right;
         Right := Temp;
      end Swap;
   
   ---------------------------------------------------------------------------------------
       function ">=" (Left : in Element_Type; Right : in Element_Type) 
       			return Boolean is
      begin 
         return not(Left < Right);
      end ">=";
   
   ---------------------------------------------------------------------------------------
       procedure Split(Values      : in out Array_Type;
       			 Split_Index :    out Positive) is
         Left  : Positive;
         Right : Positive;
      begin 
         Left  := Values'First + 1;
         Right := Values'Last;
         loop --each iteration, two out of place values are swapped
         --Left to Right search
            loop
            --exit when searches cross or find an element on wrong side
               exit when Left > Right or else
                  		  Values(Left) < Values(Values'First);
               Left := Left + 1;
            end loop;
         
         --right to left search
            loop
            --exit when searches cross or find an element on wrong side
               exit when Left > Right or 
                  		Values(Right) < Values(Values'First);
               Right := Right - 1;
            end loop;
         --exit outer loop when searches cross
            exit when Left > Right;
         --swap the two values on the wrong side of the split value
            Swap(Values(Left), Values(Right));
            Left := Left + 1;
            Right := Right -1;
         end loop;
      	-- move split value to proper location
         Swap(Values(Values'First), Values(Right));
      		--return the index of the values that divides the two portions
         Split_Index := Right;
      End Split;
   ------------------------------------------------------------------------------
      Split_Index : Positive;
   begin 
      if Values'Length > 1 then
         Split(Values, Split_Index);
         Quick_Sort(Values(Values'First..Split_Index -1 ));
         Quick_Sort(Values(Split_Index + 1..Values'Last));
      end if;
   end Quick_Sort;



```

```

with Ada.Text_IO;
with Ada.Integer_Text_IO;
with Quick_Sort;

procedure Quick_Sort_Test is
	type Integer_Array is array(1..14) of Integer;
	myArr : array(1..14) of Integer;
begin 
	myArr := (9,20,8,14,10,6,60,11,23,-4,13,58,0,35);
	Quick_Sort.Quick_Sort(myArr);
end Quick_Sort_Test;
	

```

any help would be great. 

Thanks,
Hunter.

---

