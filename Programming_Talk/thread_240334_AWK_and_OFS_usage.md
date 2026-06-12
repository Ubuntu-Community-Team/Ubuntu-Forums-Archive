---
title: "AWK and OFS usage"
date: 2006-08-20
forum: Programming Talk
---

### Post by Browser_ice on 2006-08-20
This weekend I am coding a AWK script that I want to use at the office (IBM AIX UNIX machine).

When I set the OFS to "," and print variables, the OFS isn't taken in account. Is this Ubuntu's doing ? The output generated contains spaces between each printed fields insted of ",". Why ?

[INDENT]#!/usr/bin/awk -f
BEGIN{
	FS=" ";
	OFS=",";
	PlanID="";
	ReturnCode="";
	Status="";
	PlanName="";
	StartedAt="";
	EndedAt="";
	OutputRec="";
}
...
IF ( Error=="no" )
	{
#	STANDARD OUTPUT RECORD FOUND
	PRINT PlanID ReturnCode Status PlanName StartedAt EndedAt;
	}
ELSE
	{
#	NON STANDARD OUTPUT RECORD FOUND
	PRINT Error;
	}
#
END{} [/INDENT]

---

### Post by Browser_ice on 2006-08-20
Hummm, the problem seams to be more then that.

I added a print that should get executed at each pass but nothing happens. I think my code isn't run at all. Calling my awk script simply list the whole input file content without any changes.

Any one care to check my script ? Its my first AWK script.

I execute it this way :
>awk -f CleanPlanOutput.sh wmonpln.output

Source code :
[INDENT]#!/usr/bin/awk -f
BEGIN{
	FS=" ";
	OFS=",";
	PlanID="";
	ReturnCode="";	Status="";
	PlanName="";
	StartedAt="";
	EndedAt="";
	OutputRec="";
	RecNumb=0;
}
{
#<-----PlanID------>  ReturnCode <--Status------> <-------PlanName-----------------------------------------------------------> <----StartedAt---->  <------EndedAt----->
#1155772582033163865  0          Canceled Pending UK_REM_EMD_ms_std_hotfix_sequence_NET_part1_ALL_2006-08-15@08/17/06 01:56:22 2006-08-17 01:56:22  2006-08-18  01:58:21 

#Field#1              2          3        4       5                                                                   6        7          8         9           10
#1155772659085890842  0          Canceled         UK_REM_EMD_ms_std_hotfix_sequence_NET_part2_ALL_2006-08-15@08/17/06 01:57:39 2006-08-17 01:57:39  2006-08-18  02:00:34 

#Field#1              2          3                4                                                                   5        6          7         8           9
#
IF ( NF==10 ) 
	{
#	CHECK FOR PENDING WORD ADDED IN STATUS
	IF ( $4 == "Pending" )
		{
#		YEP WE HAVE A DOUBLE WORD TYPE OF STATUS
		PlanID=$1;
		ReturnCode=$2;
		Status=$3+" Pending";
		PlanName=$5+" "+$6;
		StartedAt=$7+" "+$8;
		EndedAt=$9+" "+$10;
		Error="no";
		}
	ELSE
		{
#		NOPE WE HAVE NON STANDARD RECORD
		Error="Unknown Status:"+$1+" "+$2+" "+$3+" "+$4+" "+$5+" "+$6+" "+$7+" "+$8+" "+$9+" "+$10;
		}
	}
ELSE	IF ( NF==9 )
		{
#		NORMAL STATUS TYPE OF RECORD
		PlanID=$1;
		ReturnCode=$2;
		Status=$3;
		PlanName=$4+" "5;
		StartedAt=$6+" "+$7;
		EndedAt=$8+" "+$9;
		Error="no";
		}
	ELSE 	Error="ERROR: NONE STANDARD RECORD FOUND!:"+$1;
		}
#
# OK WE GOT THE INFO, TIME TO PRINT IT
#
RecNumb=RecNumb+1;
PRINTf "Record number:%d",RecNumb; 

IF ( Error=="no" )
	{
#	STANDARD OUTPUT RECORD FOUND
	PRINT PlanID ReturnCode Status PlanName StartedAt EndedAt;
	}
ELSE
	{
#	NON STANDARD OUTPUT RECORD FOUND
	PRINT Error;
	}
#
}
END{}
[/INDENT]

---

