---
title: "Insert a date in an sql transaction"
date: 2010-04-02
forum: Programming Talk
---

### Post by Shpongle on 2010-04-02
Hey all , im trying to insert a date into an oracle database by running a transaction using the following code, the transaction will then be put into a procedure and executed by a java program via a gui based calender.

i keep getting this error  below , i am putting the date in as 
2010/12/22 and it will let me insert it normally like this
(to_date('2012/12/22,'YYYY/MM/DD')) but its not letting me do it on the transaction despite me defining the start date variable with '' , as '&stdate'



OCI-01861:
literal does not match format string
Cause:	 Literals in the input must be the same length as literals in the format string (with the exception of leading whitespace). If the "FX" modifier has been toggled on, the literal must match exactly, with no extra whitespace.
Action:	 Correct the format string to match the literal. 




i have highlighted the lines in question

--Calender Entry transaction
DECLARE 

   ent Calender_Entry.Entry_ID%TYPE:= &ent;
   staff Calender_Entry.Staff_ID%TYPE:= &staff;
  [COLOR="Red"] stdate Calender_Entry.Start_Date%TYPE:= '&stdate';[/COLOR]
   sttime Calender_Entry.Start_Time%TYPE:= &sttime;
   etype Calender_Entry.Entry_Type%TYPE:= '&etype';
   recur Calender_Entry.Recurring%TYPE:='&recur';
   det	Calender_Entry.Details%TYPE:='&det';
   fntime Calender_Entry.Finish_Time%TYPE:= &fntime;
BEGIN
--Add a calender entry
INSERT INTO Calender_Entry VALUES (ent, staff,[COLOR="Red"]( to_date(stdate,'YYYY/MM/DD')),[/COLOR]
  sttime, etype ,recur,det, fntime);
  

COMMIT;
END;


 this is the table it modifies


CREATE TABLE Calender_Entry
(
	Entry_ID	  INTEGER  NOT NULL ,
	Staff_ID	  INTEGER  NOT NULL ,
	Start_Date	  DATE  NOT NULL ,
	Start_Time	  INTEGER  NOT NULL ,
	Entry_Type	  VARCHAR2(20)  NOT NULL CHECK (Entry_Type IN ('Lecture', 'Meeting' , 'Appointment')) ,
	Recurring	  CHAR  NOT NULL CHECK (Recurring IN('Y','N')),
	Details		  VARCHAR2(100)  NULL ,
	Finish_Time	  NUMBER(4)  NULL ,
CONSTRAINT  XPKCalender_Entry PRIMARY KEY (Entry_ID),
CONSTRAINT  R_2 FOREIGN KEY (Staff_ID) REFERENCES Staff(Staff_ID)
);


any help is greatly appreciated

---

### Post by ratcheer on 2010-04-02
Hmmm, at first glance it looks correct to me, too. I was an Oracle DBA for 14 years until last Fall, when I lost my job in the economy mess. I now have no Oracle system on which to test to try to see what the problem is. Sorry.

Tim

---

### Post by Shpongle on 2010-04-02
thanks anyway , and sorry to hear about your job :-( , iv been all over the net trying to figure it out but they all show hard coded transactions / to date functions . il keep looking anyway

---

