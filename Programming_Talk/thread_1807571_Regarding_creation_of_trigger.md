---
title: "Regarding creation of trigger"
date: 2011-07-19
forum: Programming Talk
---

### Post by vjohnny8 on 2011-07-19
Hi everyone,
There will be no gap concept in the dates as given below. it will take the current rate of the max date that is currently present in the database i.e
14-jul-11 2.5 
13-jul-11 3.5 5.6
the 2 above rows are currently present in the database, now if a new row is inserted as below,
date curr_rate prev_rate
17-jul-11 1.5 2.5
then the previous rate that is shown for 17th jul, is the current rate of 14th jul ( which is already present in the database)
so in simple terms, the previous rate of 17 jul should display the value of the current rate of the max date already present in the database.
how can i modify the below trigger to achieve this ?
 
create table t1
( index_id number,
time_vertex number,
date1 date,
date_rate number(10,2),
prev_rate number(10,2) )
 
create or replace trigger t1_ai before insert on t1 for each row
begin
begin
Select date_rate 
into :new.prev_rate
from t1
where rowid in 
(select rn from
(select rowid rn, dense_rank() over (partition by index_id,time_vertex order by date1 desc) rnk from t1
where index_id = :new.index_id and
time_vertex = :new.time_vertex and 
date1 < :new.date1
) where rnk =1 );
exception when no_data_found then 
:new.prev_rate := -1;
end; 
end;

---

### Post by PaulM1985 on 2011-07-19
Why use a trigger and store this data in a row?  Why not have a query which finds the date before a supplied date and gets the value from that?  This would save on having to duplicate the information in your table.

Your select statement seems pretty complicated in your example.  Don't you just want the first row before the date you supply. MAX(date) < dateForNewRow?

Additionally, when you add code can you put it in CODE tags (use the # button on the interface where you post).

Secondly, is this a duplicate post of your original request?

Paul

---

### Post by vjohnny8 on 2011-07-19
[LEFT]Hi PaulM1985,
 
Thanks for your reply. Could you please provide the code in oracle, as to how to achieve this ?
 
Thanks !!!![/LEFT]

---

### Post by PaulM1985 on 2011-07-19
> **vjohnny8 said:**
> [LEFT]Hi PaulM1985,
 
Thanks for your reply. Could you please provide the code in oracle, as to how to achieve this ?
 
Thanks !!!![/LEFT]

Yeh, sure no problem.

Actually, I have some homework due in at the end of the month.  If you could possibly provide me all the answers to that, then yeh, I'll send the code straight across.

Please make an effort.
I asked you about why you needed a trigger, you came back with no response.
I made a suggestion about how complicated your query seemed to be and gave you a little hint about what I think you are after and you ignored it.
You just asked me to provide you with the solution.
This made me think you are just fishing for homework answers.

Paul

---

