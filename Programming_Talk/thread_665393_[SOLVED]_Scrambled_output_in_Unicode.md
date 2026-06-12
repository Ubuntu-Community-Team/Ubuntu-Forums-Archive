---
title: "[SOLVED] Scrambled output in Unicode"
date: 2008-01-12
forum: Programming Talk
---

### Post by quandary on 2008-01-12
Hi!
I'm trying to get date, time, and weekday seperate.
Now I managed to do that, but I got problems when compiling and using  Russian language.
So I intended to switch to Unicode for the few Russian words.
However, the output is scrambled...

This is the output:
```

root@googlebot:~/Desktop# ./main
Datum: Samstag, 12.1.2008, 16:35:12 (MEZ)
Date: Saturday, 1/12/2008, 16:35:12 (CET)
Date: Samedi, 12.1.2008, 16:35:12 (HEC)
&#1076;&#1072;&#1090;&#1072;: 0x804975c, 12.1.2008, 16:35:12 0x804958c
40B0: !C11>B0, 12.1.2008, 16:35:12 (&)
Fecha: Sábado, 12.1.2008, 16:35:12 (HEC)
Dies ist der 12. Tag im Jahr.
This is the 12th day in the year.
C'est le 12ième jour dans l'année.
&#1069;&#1090;&#1086; 12. &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;.
Este es el 12. día en el año.
root@googlebot:~/Desktop# 

```
Why do i get 0x8049560 in the first place, and 40B0: !C11>B0 when using wcout?

This is the C++ program:
```

#include <iostream>
#include <ctime>


struct timeinfo_t
{
	int day ;
	int month ;
	int year ;
	int hours ;
	int minutes ;
	int seconds ;
	int weekDayNumber ;
	int dayInYear ;
	int daylightSavingTime ;
	
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	wchar_t* weekDay_ru ;
    char* weekDay_sp ;
    
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
};

timeinfo_t GetTime()
{
	time_t sysTime ;
	tm *tmptr_CurrentTime ;
	sysTime = time(NULL) ;
	tmptr_CurrentTime = localtime(&sysTime) ; // for localized time
	//tmptr_CurrentTime = gmtime(&sysTime) ; // for GMT
	
	// Convert
	int weekDayNumber = tmptr_CurrentTime->tm_wday ;  // days since Sunday 0..6
	int daylightSavingTime = tmptr_CurrentTime->tm_isdst ; // Daylight Saving Time flag, 0 = winterTime, 1 = summerTime; 
	// GMT has no Daylight Saving Time
	
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	wchar_t* weekDay_ru ;
	char* weekDay_sp ;
	
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
	
	if (daylightSavingTime) // 1 for summer time, at least for CET
	{
		daylightSaving_de="(MESZ)" ; // Mitteleuropäische Sommerzeit
		daylightSaving_en="(CEST)" ; // Central European Summer Time
		daylightSaving_fr="(HECE)" ; // Heure d'Europe centrale d’été
		daylightSaving_ru= L"(&#1062;&#1045;&#1051;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1083;&#1077;&#1090;&#1085;&#1077;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HECV)" ; // Hora del Europa Central de verano
	}
	else
	{
		daylightSaving_de="(MEZ)" ; // Mitteleuropäische Zeit
		daylightSaving_en="(CET)" ; // Central European Time
		daylightSaving_fr="(HEC)" ; // Heure d'Europe centrale
		daylightSaving_ru= L"(&#1062;&#1045;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HEC)" ; // Hora del Europa Central
	}
	
	switch (weekDayNumber) // 0: Sunday, 1: Monday, 2: Tuesday, 3: Wednesday, 4: Thursday, 5: Friday, 6: Saturday
	{
		case 0:
			weekDay_de = "Sonntag" ;
			weekDay_en = "Sunday" ;  // should have used Lord's day ;-)
			weekDay_fr = "Dimanche" ;
			weekDay_ru = L"&#1042;&#1086;&#1089;&#1082;&#1088;&#1077;&#1089;&#1077;&#1085;&#1100;&#1077;" ;
			weekDay_sp = "Domingo" ;
			break;
		
		case 1: 
			weekDay_de = "Montag" ;
			weekDay_en = "Monday" ;
			weekDay_fr = "Lundi" ;
			weekDay_ru = L"&#1055;&#1086;&#1085;&#1077;&#1076;&#1077;&#1083;&#1100;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Lunes" ;
			break;
		
		case 2:
			weekDay_de = "Dienstag" ;
			weekDay_en = "Tuesday" ;
			weekDay_fr = "Mardi" ;
			weekDay_ru = L"&#1042;&#1090;&#1086;&#1088;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Martes" ;
			break;
		
		case 3:
			weekDay_de = "Mittwoch" ;
			weekDay_en = "Wednesday" ;
			weekDay_fr = "Mercredi" ;
			weekDay_ru = L"&#1057;&#1088;&#1077;&#1076;&#1072;" ;
			weekDay_sp = "Miércoles" ;
			break;
		
		case 4:
			weekDay_de = "Donnerstag" ;
			weekDay_en = "Thursday" ;
			weekDay_fr = "Jeudi" ;
			weekDay_ru = L"&#1063;&#1077;&#1090;&#1074;&#1077;&#1088;&#1075;" ;
			weekDay_sp = "Jueves" ;
			break;
		
		case 5:
			weekDay_de = "Freitag" ;
			weekDay_en = "Friday" ;
			weekDay_fr = "Vendredi" ;
			weekDay_ru = L"&#1055;&#1103;&#1090;&#1085;&#1080;&#1094;&#1072;" ;
			weekDay_sp = "Viernes" ;
			break;
		
		case 6:
			weekDay_de = "Samstag" ;
			weekDay_en = "Saturday" ;
			weekDay_fr = "Samedi" ;
			weekDay_ru = L"&#1057;&#1091;&#1073;&#1073;&#1086;&#1090;&#1072;" ;
			weekDay_sp = "Sábado" ;
			break;
		
		default: // do these if expr != any above
			weekDay_de = "Fehler" ;  
			weekDay_en = "Error" ;
			weekDay_fr = "Erreur" ; 
			weekDay_ru = L"&#1044;&#1077;&#1092;&#1077;&#1082;&#1090;" ;
			weekDay_sp = "Error" ;
	}
	// end converting
	
	timeinfo_t tmNfo_TimeToReturn;	
	
	tmNfo_TimeToReturn.day = tmptr_CurrentTime->tm_mday ;
	tmNfo_TimeToReturn.month = 1 + tmptr_CurrentTime->tm_mon ;
	tmNfo_TimeToReturn.year = 1900 + tmptr_CurrentTime->tm_year ;
	tmNfo_TimeToReturn.hours = tmptr_CurrentTime->tm_hour ;
	tmNfo_TimeToReturn.minutes = tmptr_CurrentTime->tm_min ;
	tmNfo_TimeToReturn.seconds = tmptr_CurrentTime->tm_sec ;
	tmNfo_TimeToReturn.weekDayNumber = weekDayNumber ;
	tmNfo_TimeToReturn.dayInYear = 1 + tmptr_CurrentTime->tm_yday ;  // days since January 1,  0..365 // probably 364
	tmNfo_TimeToReturn.daylightSavingTime = daylightSavingTime ;
	
	tmNfo_TimeToReturn.weekDay_de = weekDay_de ;
	tmNfo_TimeToReturn.weekDay_en = weekDay_en ;
	tmNfo_TimeToReturn.weekDay_fr = weekDay_fr ;
	tmNfo_TimeToReturn.weekDay_ru = weekDay_ru ;
	tmNfo_TimeToReturn.weekDay_sp = weekDay_sp ;
	
	tmNfo_TimeToReturn.daylightSaving_de = daylightSaving_de;
	tmNfo_TimeToReturn.daylightSaving_en = daylightSaving_en;
	tmNfo_TimeToReturn.daylightSaving_fr = daylightSaving_fr;
	tmNfo_TimeToReturn.daylightSaving_ru = daylightSaving_ru;
	tmNfo_TimeToReturn.daylightSaving_sp = daylightSaving_sp;
		
	return tmNfo_TimeToReturn ;
}


int main()
{
	timeinfo_t tmNfo_MyTime = GetTime();
	    
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_de << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_de << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_en << ", " << tmNfo_MyTime.month << "/" << tmNfo_MyTime.day << "/" << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_en << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_fr << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_fr << "\n";
	std::cout << "&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_ru << "\n";
	std::wcout << L"&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << L", "<< tmNfo_MyTime.day << L"." << tmNfo_MyTime.month << L"." << tmNfo_MyTime.year << L", " << tmNfo_MyTime.hours << L":" << tmNfo_MyTime.minutes << L":" << tmNfo_MyTime.seconds << L" "<< tmNfo_MyTime.daylightSaving_ru << L"\n";
	std::cout << "Fecha: " << tmNfo_MyTime.weekDay_sp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_sp << "\n";
	std::cout << "Dies ist der " << tmNfo_MyTime.dayInYear << ". Tag im Jahr." << std::endl ; // always correct
	std::cout << "This is the " << tmNfo_MyTime.dayInYear << "th day in the year." << std::endl ; // not correct for 1st, 2nd, 3rd, and derivatives
	std::cout << "C'est le " << tmNfo_MyTime.dayInYear << "ième jour dans l'année." << std::endl ; // not correct for ier and derivatives
	std::cout << "&#1069;&#1090;&#1086; " << tmNfo_MyTime.dayInYear << ". &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;." << std::endl ; // always correct
	std::cout << "Este es el " << tmNfo_MyTime.dayInYear << ". día en el año." << std::endl ; // don't know Spanish
}

// ----------------------------------------------

// Fields of the tm struct (C++ syntax):
/*
   struct tm
   {
       int tm_sec;   // seconds after minute 0..60
       int tm_min;   // minutes after hour 0..59
       int tm_hour;  // hours since midnight 0..23
       int tm_mday;  // day of month 1..31
       int tm_mon;   // months since January 0..11
       int tm_year;  // years since 1900
       int tm_wday;  // days since Sunday 0..6
       int tm_yday;  // days since January 1 0..365
       int tm_isdst; // Daylight Saving Time flag
   };
*/

// Declarations for gmtime and localtime functions (C++ syntax):

// tm *localtime(const time_t * timer);
// tm *gmtime(const time_t * timer);

```

---

### Post by quandary on 2008-01-12
bump

---

### Post by quandary on 2008-01-12
OK, i appended some more languages, and it gets even better:

this is the new output:
```

root@googlebot:~/Desktop# ./main
&#36039;&#26009;: 0x804a55c, 12.1.2008, 17:55:48 0x804a1b0
Datum: Samstag, 12.1.2008, 17:55:48 (MEZ)
Date: Saturday, 1/12/2008, 17:55:48 (CET)
Date: Samedi, 12.1.2008, 17:55:48 (HEC)
Data: Sabato, 12.1.2008, 17:55:48 (FOEC)
&#26085;&#20184;: 0x804a58c, 12.1.2008, 17:55:48 0x804a1e4
Datum: Zaterdag, 12.1.2008, 17:55:48 (CET)
Segmentation fault
root@googlebot:~/Desktop# 

```

this is the new file:
```

#include <iostream>
#include <ctime>


struct timeinfo_t
{
	int day ;
	int month ;
	int year ;
	int hours ;
	int minutes ;
	int seconds ;
	int weekDayNumber ;
	int dayInYear ;
	int daylightSavingTime ;
	
	wchar_t* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	wchar_t* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	wchar_t* weekDay_ru ;
    char* weekDay_sp ;
    
	wchar_t* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	wchar_t* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
};

timeinfo_t GetTime()
{
	time_t sysTime ;
	tm *tmptr_CurrentTime ;
	sysTime = time(NULL) ;
	tmptr_CurrentTime = localtime(&sysTime) ; // for localized time
	//tmptr_CurrentTime = gmtime(&sysTime) ; // for GMT
	
	// Convert
	int weekDayNumber = tmptr_CurrentTime->tm_wday ;  // days since Sunday 0..6
	int daylightSavingTime = tmptr_CurrentTime->tm_isdst ; // Daylight Saving Time flag, 0 = winterTime, 1 = summerTime; 
	// GMT has no Daylight Saving Time
	
	wchar_t* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	wchar_t* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	wchar_t* weekDay_ru ;
	char* weekDay_sp ;
	
	wchar_t* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	wchar_t* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
	
	if (daylightSavingTime) // 1 for summer time, at least for CET
	{
		daylightSaving_cn=L"(&#20013;&#27472;&#22799;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#22799;&#22825;&#26178;&#38291;
		daylightSaving_de="(MESZ)" ; // Mitteleuropäische Sommerzeit
		daylightSaving_en="(CEST)" ; // Central European Summer Time
		daylightSaving_fr="(HECE)" ; // Heure d'Europe centrale d’été
		daylightSaving_it="(OLFEC)" ; // Ora legale fuso dell'Europa Centrale  
		daylightSaving_jp= L"(&#20013;&#12520;&#22799;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#22799;&#26178;
		daylightSaving_nl="(CEZT)" ; // Centrale Europese zomertijd
		daylightSaving_pt="(HECV)" ; // Hora da Europa Central de verão 
		daylightSaving_ru= L"(&#1062;&#1045;&#1051;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1083;&#1077;&#1090;&#1085;&#1077;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HECV)" ; // Hora del Europa Central de verano
	}
	else
	{
		daylightSaving_cn= L"(&#20013;&#27472;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#26178;&#38291;
		daylightSaving_de="(MEZ)" ; // Mitteleuropäische Zeit
		daylightSaving_en="(CET)" ; // Central European Time
		daylightSaving_fr="(HEC)" ; // Heure d'Europe centrale
		daylightSaving_it="(FOEC)" ; // Fuso orario dell'Europa Centrale 
		daylightSaving_jp= L"(&#20013;&#12520;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#26178;
		daylightSaving_nl="(CET)" ; // Centrale Europese Tijd
		daylightSaving_pt="(HEC)" ; // Hora da Europa Central 
		daylightSaving_ru= L"(&#1062;&#1045;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HEC)" ; // Hora del Europa Central
	}
	
	switch (weekDayNumber) // 0: Sunday, 1: Monday, 2: Tuesday, 3: Wednesday, 4: Thursday, 5: Friday, 6: Saturday
	{
		case 0:
			weekDay_cn = L"&#26143;&#26399;&#22825;" ;
			weekDay_de = "Sonntag" ;
			weekDay_en = "Sunday" ;  // should have used Lord's day ;-)
			weekDay_fr = "Dimanche" ;
			weekDay_it = "Domenica" ;
			weekDay_jp = L"&#26085;&#26332;&#26085;" ;
			weekDay_nl = "Zondag" ;
			weekDay_no = "Søndag" ;
			weekDay_pt = "Domingo" ;
			weekDay_ru = L"&#1042;&#1086;&#1089;&#1082;&#1088;&#1077;&#1089;&#1077;&#1085;&#1100;&#1077;" ;
			weekDay_sp = "Domingo" ;
			break;
		
		case 1: 
			weekDay_cn = L"&#26143;&#26399;&#19968;" ;
			weekDay_de = "Montag" ;
			weekDay_en = "Monday" ;
			weekDay_fr = "Lundi" ;
			weekDay_it = "Lunedì" ;
			weekDay_jp = L"&#26376;&#26332;&#26085;" ;
			weekDay_nl = "Maandag" ;
			weekDay_no = "Mandag" ;
			weekDay_pt = "Segunda-feira" ;
			weekDay_ru = L"&#1055;&#1086;&#1085;&#1077;&#1076;&#1077;&#1083;&#1100;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Lunes" ;
			break;
		
		case 2:
			weekDay_cn = L"&#26143;&#26399;&#20108;" ;
			weekDay_de = "Dienstag" ;
			weekDay_en = "Tuesday" ;
			weekDay_fr = "Mardi" ;
			weekDay_it = "Martedì" ;
			weekDay_jp = L"&#28779;&#26332;&#26085;" ;
			weekDay_nl = "Dinsdag" ;
			weekDay_no = "Tirsdag" ;
			weekDay_pt = "Terça-feira" ;
			weekDay_ru = L"&#1042;&#1090;&#1086;&#1088;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Martes" ;
			break;
		
		case 3:
			weekDay_cn = L"&#26143;&#26399;&#19977;" ;
			weekDay_de = "Mittwoch" ;
			weekDay_en = "Wednesday" ;
			weekDay_fr = "Mercredi" ;
			weekDay_it = "Mercoledì" ;
			weekDay_jp = L"&#27700;&#26332;&#26085;" ;
			weekDay_nl = "Woensdag" ;
			weekDay_no = "Onsdag" ;
			weekDay_pt = "Quarta-feira" ;
			weekDay_ru = L"&#1057;&#1088;&#1077;&#1076;&#1072;" ;
			weekDay_sp = "Miércoles" ;
			break;
		
		case 4:
			weekDay_cn = L"&#26143;&#26399;&#22235;" ;
			weekDay_de = "Donnerstag" ;
			weekDay_en = "Thursday" ;
			weekDay_fr = "Jeudi" ;
			weekDay_it = "Giovedì" ;
			weekDay_jp = L"&#26408;&#26332;&#26085;" ;
			weekDay_nl = "Donderdag" ;
			weekDay_no = "Torsdag" ;
			weekDay_pt = "Quinta-feira" ;
			weekDay_ru = L"&#1063;&#1077;&#1090;&#1074;&#1077;&#1088;&#1075;" ;
			weekDay_sp = "Jueves" ;
			break;
		
		case 5:
			weekDay_cn = L"&#26143;&#26399;&#20116;" ;
			weekDay_de = "Freitag" ;
			weekDay_en = "Friday" ;
			weekDay_fr = "Vendredi" ;
			weekDay_it = "Venerdì" ;
			weekDay_jp = L"&#37329;&#26332;&#26085;" ;
			weekDay_nl = "Vrijdag" ;
			weekDay_no = "Fredag" ;
			weekDay_pt = "Sexta-feira" ;
			weekDay_ru = L"&#1055;&#1103;&#1090;&#1085;&#1080;&#1094;&#1072;" ;
			weekDay_sp = "Viernes" ;
			break;
		
		case 6:
			weekDay_cn = L"&#26143;&#26399;&#20845;" ;
			weekDay_de = "Samstag" ;
			weekDay_en = "Saturday" ;
			weekDay_fr = "Samedi" ;
			weekDay_it = "Sabato" ;
			weekDay_jp = L"&#22303;&#26332;&#26085;&#12395;" ;
			weekDay_nl = "Zaterdag" ;
			weekDay_no = "Lørdag" ;
			weekDay_pt = "Sábado" ;
			weekDay_ru = L"&#1057;&#1091;&#1073;&#1073;&#1086;&#1090;&#1072;" ;
			weekDay_sp = "Sábado" ;
			break;
		
		default: // do these if expr != any above
			weekDay_cn = L"&#37679;&#35492;" ;
			weekDay_de = "Fehler" ;  
			weekDay_en = "Error" ;
			weekDay_fr = "Erreur" ; 
			weekDay_it = "Errore" ;
			weekDay_jp = L"&#12456;&#12521;&#12540;&#12308;&#35492;&#12426;&#12309;" ;
			weekDay_nl = "De fout" ;
			weekDay_no = "Feil" ;
			weekDay_pt = "Erro" ;
			weekDay_ru = L"&#1044;&#1077;&#1092;&#1077;&#1082;&#1090;" ;
			weekDay_sp = "Error" ;
	}
	// end converting
	
	timeinfo_t tmNfo_TimeToReturn;	
	
	tmNfo_TimeToReturn.day = tmptr_CurrentTime->tm_mday ;
	tmNfo_TimeToReturn.month = 1 + tmptr_CurrentTime->tm_mon ;
	tmNfo_TimeToReturn.year = 1900 + tmptr_CurrentTime->tm_year ;
	tmNfo_TimeToReturn.hours = tmptr_CurrentTime->tm_hour ;
	tmNfo_TimeToReturn.minutes = tmptr_CurrentTime->tm_min ;
	tmNfo_TimeToReturn.seconds = tmptr_CurrentTime->tm_sec ;
	tmNfo_TimeToReturn.weekDayNumber = weekDayNumber ;
	tmNfo_TimeToReturn.dayInYear = 1 + tmptr_CurrentTime->tm_yday ;  // days since January 1,  0..365 // probably 364
	tmNfo_TimeToReturn.daylightSavingTime = daylightSavingTime ;
	
	tmNfo_TimeToReturn.weekDay_cn = weekDay_cn ;
	tmNfo_TimeToReturn.weekDay_de = weekDay_de ;
	tmNfo_TimeToReturn.weekDay_en = weekDay_en ;
	tmNfo_TimeToReturn.weekDay_fr = weekDay_fr ;
	tmNfo_TimeToReturn.weekDay_it = weekDay_it ;
	tmNfo_TimeToReturn.weekDay_jp = weekDay_jp ;
	tmNfo_TimeToReturn.weekDay_nl = weekDay_nl ;
	tmNfo_TimeToReturn.weekDay_no = weekDay_no ;
	tmNfo_TimeToReturn.weekDay_pt = weekDay_pt ;
	tmNfo_TimeToReturn.weekDay_ru = weekDay_ru ;
	tmNfo_TimeToReturn.weekDay_sp = weekDay_sp ;
	
	tmNfo_TimeToReturn.daylightSaving_cn = daylightSaving_cn;
	tmNfo_TimeToReturn.daylightSaving_de = daylightSaving_de;
	tmNfo_TimeToReturn.daylightSaving_en = daylightSaving_en;
	tmNfo_TimeToReturn.daylightSaving_fr = daylightSaving_fr;
	tmNfo_TimeToReturn.daylightSaving_it = daylightSaving_it;
	tmNfo_TimeToReturn.daylightSaving_nl = daylightSaving_nl;
	tmNfo_TimeToReturn.daylightSaving_no = daylightSaving_no;
	tmNfo_TimeToReturn.daylightSaving_jp = daylightSaving_jp;
	tmNfo_TimeToReturn.daylightSaving_pt = daylightSaving_pt;
	tmNfo_TimeToReturn.daylightSaving_ru = daylightSaving_ru;
	tmNfo_TimeToReturn.daylightSaving_sp = daylightSaving_sp;
		
	return tmNfo_TimeToReturn ;
}


int main()
{
	timeinfo_t tmNfo_MyTime = GetTime();
	    
	std::cout << "&#36039;&#26009;: " << tmNfo_MyTime.weekDay_cn << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_cn << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_de << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_de << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_en << ", " << tmNfo_MyTime.month << "/" << tmNfo_MyTime.day << "/" << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_en << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_fr << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_fr << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_it << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_it << "\n";
	std::cout << "&#26085;&#20184;: " << tmNfo_MyTime.weekDay_jp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_jp << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_nl << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_nl << "\n";
	std::cout << "Dato: " << tmNfo_MyTime.weekDay_no << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_no << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_pt << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_pt << "\n";
	std::cout << "&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_ru << "\n";
	std::wcout << L"&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << L", "<< tmNfo_MyTime.day << L"." << tmNfo_MyTime.month << L"." << tmNfo_MyTime.year << L", " << tmNfo_MyTime.hours << L":" << tmNfo_MyTime.minutes << L":" << tmNfo_MyTime.seconds << L" "<< tmNfo_MyTime.daylightSaving_ru << L"\n";
	std::cout << "Fecha: " << tmNfo_MyTime.weekDay_sp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_sp << "\n";
	
	std::cout << "&#36889;&#26159;&#24180;&#30340;&#31532; " << tmNfo_MyTime.dayInYear << ". &#22825;&#12290;" << std::endl ; // not correct for first   //cn
	std::cout << "Dies ist der " << tmNfo_MyTime.dayInYear << ". Tag im Jahr." << std::endl ; // always correct // de
	std::cout << "This is the " << tmNfo_MyTime.dayInYear << "th day in the year." << std::endl ; // not correct for 1st, 2nd, 3rd, and derivatives //en
	std::cout << "C'est le " << tmNfo_MyTime.dayInYear << "ième jour dans l'année." << std::endl ; // not correct for ier //fr
	std::cout << "Questo è il " << tmNfo_MyTime.dayInYear << " giorno nell'anno." << std::endl ; // don't know Italian // it
	std::cout << "&#12371;&#12428;&#12399; " << tmNfo_MyTime.dayInYear << " &#26085;&#30446;&#12395;&#12381;&#12398;&#24180;&#12395;&#12391;&#12377;&#12290;" << std::endl ; // don't know Japanese, but looks like it's always correct // jp
	std::cout << "Dit is de " << tmNfo_MyTime.dayInYear << ". dag in het jaar." << std::endl ; // don't know Dutch, but probably like German // nl
	std::cout << "Dette er " << tmNfo_MyTime.dayInYear << ". dagen i året." << std::endl ; // don't know Norwegian // no
	std::cout << "Isto é o " << tmNfo_MyTime.dayInYear << ". dia o ano." << std::endl ; // don't know Portugues // pt
	std::cout << "&#1069;&#1090;&#1086; " << tmNfo_MyTime.dayInYear << ". &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;." << std::endl ; // always correct // ru
	std::cout << "Este es el " << tmNfo_MyTime.dayInYear << ". día en el año." << std::endl ; // don't know Spanish // sp
}

// ----------------------------------------------

// Fields of the tm struct (C++ syntax):
/*
   struct tm
   {
       int tm_sec;   // seconds after minute 0..60
       int tm_min;   // minutes after hour 0..59
       int tm_hour;  // hours since midnight 0..23
       int tm_mday;  // day of month 1..31
       int tm_mon;   // months since January 0..11
       int tm_year;  // years since 1900
       int tm_wday;  // days since Sunday 0..6
       int tm_yday;  // days since January 1 0..365
       int tm_isdst; // Daylight Saving Time flag
   };
*/

// Declarations for gmtime and localtime functions (C++ syntax):

// tm *localtime(const time_t * timer);
// tm *gmtime(const time_t * timer);

```

---

### Post by stroyan on 2008-01-12
The segmentation fault happens because you are printing daylightSaving_no and you didn't initialize it.

---

### Post by quandary on 2008-01-12
Oh f***, thanks! Corrected it.

Now no more segmentation fault, but only the old problem:

The scrambled characters output:  (0x804a57c looks like an address...)
```

root@googlebot:~/Desktop# ./main
&#36039;&#26009;: 0x804a57c, 12.1.2008, 19:1:21 0x804a1c8
Datum: Samstag, 12.1.2008, 19:1:21 (MEZ)
Date: Saturday, 1/12/2008, 19:1:21 (CET)
Date: Samedi, 12.1.2008, 19:1:21 (HEC)
Data: Sabato, 12.1.2008, 19:1:21 (FOEC)
&#26085;&#20184;: 0x804a5ac, 12.1.2008, 19:1:21 0x804a1fc
Datum: Zaterdag, 12.1.2008, 19:1:21 (CET)
Dato: Lørdag, 12.1.2008, 19:1:21 (MET)
Data: Sábado, 12.1.2008, 19:1:21 (HEC)
&#1076;&#1072;&#1090;&#1072;: 0x804a5dc, 12.1.2008, 19:1:21 0x804a21c
40B0: !C11>B0, 12.1.2008, 19:1:21 (&)
Fecha: Sábado, 12.1.2008, 19:1:21 (HEC)
&#36889;&#26159;&#24180;&#30340;&#31532; 12. &#22825;&#12290;
Dies ist der 12. Tag im Jahr.
This is the 12th day in the year.
C'est le 12ième jour dans l'année.
Questo è il 12 giorno nell'anno.
&#12371;&#12428;&#12399; 12 &#26085;&#30446;&#12395;&#12381;&#12398;&#24180;&#12395;&#12391;&#12377;&#12290;
Dit is de 12. dag in het jaar.
Dette er 12. dagen i året.
Isto é o 12. dia o ano.
&#1069;&#1090;&#1086; 12. &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;.
Este es el 12. día en el año.
root@googlebot:~/Desktop# 

```


This is the code which now corrected daylight saving for Norsk.
```

#include <iostream>
#include <ctime>


struct timeinfo_t
{
	int day ;
	int month ;
	int year ;
	int hours ;
	int minutes ;
	int seconds ;
	int weekDayNumber ;
	int dayInYear ;
	int daylightSavingTime ;
	
	wchar_t* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	wchar_t* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	wchar_t* weekDay_ru ;
    char* weekDay_sp ;
    
	wchar_t* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	wchar_t* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
};

timeinfo_t GetTime()
{
	time_t sysTime ;
	tm *tmptr_CurrentTime ;
	sysTime = time(NULL) ;
	tmptr_CurrentTime = localtime(&sysTime) ; // for localized time
	//tmptr_CurrentTime = gmtime(&sysTime) ; // for GMT
	
	// Convert
	int weekDayNumber = tmptr_CurrentTime->tm_wday ;  // days since Sunday 0..6
	int daylightSavingTime = tmptr_CurrentTime->tm_isdst ; // Daylight Saving Time flag, 0 = winterTime, 1 = summerTime; 
	// GMT has no Daylight Saving Time
	
	wchar_t* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	wchar_t* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	wchar_t* weekDay_ru ;
	char* weekDay_sp ;
	
	wchar_t* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	wchar_t* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	wchar_t* daylightSaving_ru;
	char* daylightSaving_sp;
	
	if (daylightSavingTime) // 1 for summer time, at least for CET
	{
		daylightSaving_cn=L"(&#20013;&#27472;&#22799;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#22799;&#22825;&#26178;&#38291;
		daylightSaving_de="(MESZ)" ; // Mitteleuropäische Sommerzeit
		daylightSaving_en="(CEST)" ; // Central European Summer Time
		daylightSaving_fr="(HECE)" ; // Heure d'Europe centrale d’été
		daylightSaving_it="(OLFEC)" ; // Ora legale fuso dell'Europa Centrale  
		daylightSaving_jp= L"(&#20013;&#12520;&#22799;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#22799;&#26178;
		daylightSaving_no="(MEST)" ; // Mellom-europeisk Sommertid
		daylightSaving_nl="(CEZT)" ; // Centrale Europese zomertijd
		daylightSaving_pt="(HECV)" ; // Hora da Europa Central de verão 
		daylightSaving_ru= L"(&#1062;&#1045;&#1051;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1083;&#1077;&#1090;&#1085;&#1077;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HECV)" ; // Hora del Europa Central de verano
	}
	else
	{
		daylightSaving_cn= L"(&#20013;&#27472;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#26178;&#38291;
		daylightSaving_de="(MEZ)" ; // Mitteleuropäische Zeit
		daylightSaving_en="(CET)" ; // Central European Time
		daylightSaving_fr="(HEC)" ; // Heure d'Europe centrale
		daylightSaving_it="(FOEC)" ; // Fuso orario dell'Europa Centrale 
		daylightSaving_jp= L"(&#20013;&#12520;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#26178;
		daylightSaving_no="(MET)" ; // Mellom-europeisk Tid
		daylightSaving_nl="(CET)" ; // Centrale Europese Tijd
		daylightSaving_pt="(HEC)" ; // Hora da Europa Central 
		daylightSaving_ru= L"(&#1062;&#1045;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HEC)" ; // Hora del Europa Central
	}
	
	switch (weekDayNumber) // 0: Sunday, 1: Monday, 2: Tuesday, 3: Wednesday, 4: Thursday, 5: Friday, 6: Saturday
	{
		case 0:
			weekDay_cn = L"&#26143;&#26399;&#22825;" ;
			weekDay_de = "Sonntag" ;
			weekDay_en = "Sunday" ;  // should have used Lord's day ;-)
			weekDay_fr = "Dimanche" ;
			weekDay_it = "Domenica" ;
			weekDay_jp = L"&#26085;&#26332;&#26085;" ;
			weekDay_nl = "Zondag" ;
			weekDay_no = "Søndag" ;
			weekDay_pt = "Domingo" ;
			weekDay_ru = L"&#1042;&#1086;&#1089;&#1082;&#1088;&#1077;&#1089;&#1077;&#1085;&#1100;&#1077;" ;
			weekDay_sp = "Domingo" ;
			break;
		
		case 1: 
			weekDay_cn = L"&#26143;&#26399;&#19968;" ;
			weekDay_de = "Montag" ;
			weekDay_en = "Monday" ;
			weekDay_fr = "Lundi" ;
			weekDay_it = "Lunedì" ;
			weekDay_jp = L"&#26376;&#26332;&#26085;" ;
			weekDay_nl = "Maandag" ;
			weekDay_no = "Mandag" ;
			weekDay_pt = "Segunda-feira" ;
			weekDay_ru = L"&#1055;&#1086;&#1085;&#1077;&#1076;&#1077;&#1083;&#1100;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Lunes" ;
			break;
		
		case 2:
			weekDay_cn = L"&#26143;&#26399;&#20108;" ;
			weekDay_de = "Dienstag" ;
			weekDay_en = "Tuesday" ;
			weekDay_fr = "Mardi" ;
			weekDay_it = "Martedì" ;
			weekDay_jp = L"&#28779;&#26332;&#26085;" ;
			weekDay_nl = "Dinsdag" ;
			weekDay_no = "Tirsdag" ;
			weekDay_pt = "Terça-feira" ;
			weekDay_ru = L"&#1042;&#1090;&#1086;&#1088;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Martes" ;
			break;
		
		case 3:
			weekDay_cn = L"&#26143;&#26399;&#19977;" ;
			weekDay_de = "Mittwoch" ;
			weekDay_en = "Wednesday" ;
			weekDay_fr = "Mercredi" ;
			weekDay_it = "Mercoledì" ;
			weekDay_jp = L"&#27700;&#26332;&#26085;" ;
			weekDay_nl = "Woensdag" ;
			weekDay_no = "Onsdag" ;
			weekDay_pt = "Quarta-feira" ;
			weekDay_ru = L"&#1057;&#1088;&#1077;&#1076;&#1072;" ;
			weekDay_sp = "Miércoles" ;
			break;
		
		case 4:
			weekDay_cn = L"&#26143;&#26399;&#22235;" ;
			weekDay_de = "Donnerstag" ;
			weekDay_en = "Thursday" ;
			weekDay_fr = "Jeudi" ;
			weekDay_it = "Giovedì" ;
			weekDay_jp = L"&#26408;&#26332;&#26085;" ;
			weekDay_nl = "Donderdag" ;
			weekDay_no = "Torsdag" ;
			weekDay_pt = "Quinta-feira" ;
			weekDay_ru = L"&#1063;&#1077;&#1090;&#1074;&#1077;&#1088;&#1075;" ;
			weekDay_sp = "Jueves" ;
			break;
		
		case 5:
			weekDay_cn = L"&#26143;&#26399;&#20116;" ;
			weekDay_de = "Freitag" ;
			weekDay_en = "Friday" ;
			weekDay_fr = "Vendredi" ;
			weekDay_it = "Venerdì" ;
			weekDay_jp = L"&#37329;&#26332;&#26085;" ;
			weekDay_nl = "Vrijdag" ;
			weekDay_no = "Fredag" ;
			weekDay_pt = "Sexta-feira" ;
			weekDay_ru = L"&#1055;&#1103;&#1090;&#1085;&#1080;&#1094;&#1072;" ;
			weekDay_sp = "Viernes" ;
			break;
		
		case 6:
			weekDay_cn = L"&#26143;&#26399;&#20845;" ;
			weekDay_de = "Samstag" ;
			weekDay_en = "Saturday" ;
			weekDay_fr = "Samedi" ;
			weekDay_it = "Sabato" ;
			weekDay_jp = L"&#22303;&#26332;&#26085;&#12395;" ;
			weekDay_nl = "Zaterdag" ;
			weekDay_no = "Lørdag" ;
			weekDay_pt = "Sábado" ;
			weekDay_ru = L"&#1057;&#1091;&#1073;&#1073;&#1086;&#1090;&#1072;" ;
			weekDay_sp = "Sábado" ;
			break;
		
		default: // do these if expr != any above
			weekDay_cn = L"&#37679;&#35492;" ;
			weekDay_de = "Fehler" ;  
			weekDay_en = "Error" ;
			weekDay_fr = "Erreur" ; 
			weekDay_it = "Errore" ;
			weekDay_jp = L"&#12456;&#12521;&#12540;&#12308;&#35492;&#12426;&#12309;" ;
			weekDay_nl = "De fout" ;
			weekDay_no = "Feil" ;
			weekDay_pt = "Erro" ;
			weekDay_ru = L"&#1044;&#1077;&#1092;&#1077;&#1082;&#1090;" ;
			weekDay_sp = "Error" ;
	}
	// end converting
	
	timeinfo_t tmNfo_TimeToReturn;	
	
	tmNfo_TimeToReturn.day = tmptr_CurrentTime->tm_mday ;
	tmNfo_TimeToReturn.month = 1 + tmptr_CurrentTime->tm_mon ;
	tmNfo_TimeToReturn.year = 1900 + tmptr_CurrentTime->tm_year ;
	tmNfo_TimeToReturn.hours = tmptr_CurrentTime->tm_hour ;
	tmNfo_TimeToReturn.minutes = tmptr_CurrentTime->tm_min ;
	tmNfo_TimeToReturn.seconds = tmptr_CurrentTime->tm_sec ;
	tmNfo_TimeToReturn.weekDayNumber = weekDayNumber ;
	tmNfo_TimeToReturn.dayInYear = 1 + tmptr_CurrentTime->tm_yday ;  // days since January 1,  0..365 // probably 364
	tmNfo_TimeToReturn.daylightSavingTime = daylightSavingTime ;
	
	tmNfo_TimeToReturn.weekDay_cn = weekDay_cn ;
	tmNfo_TimeToReturn.weekDay_de = weekDay_de ;
	tmNfo_TimeToReturn.weekDay_en = weekDay_en ;
	tmNfo_TimeToReturn.weekDay_fr = weekDay_fr ;
	tmNfo_TimeToReturn.weekDay_it = weekDay_it ;
	tmNfo_TimeToReturn.weekDay_jp = weekDay_jp ;
	tmNfo_TimeToReturn.weekDay_nl = weekDay_nl ;
	tmNfo_TimeToReturn.weekDay_no = weekDay_no ;
	tmNfo_TimeToReturn.weekDay_pt = weekDay_pt ;
	tmNfo_TimeToReturn.weekDay_ru = weekDay_ru ;
	tmNfo_TimeToReturn.weekDay_sp = weekDay_sp ;
	
	tmNfo_TimeToReturn.daylightSaving_cn = daylightSaving_cn;
	tmNfo_TimeToReturn.daylightSaving_de = daylightSaving_de;
	tmNfo_TimeToReturn.daylightSaving_en = daylightSaving_en;
	tmNfo_TimeToReturn.daylightSaving_fr = daylightSaving_fr;
	tmNfo_TimeToReturn.daylightSaving_it = daylightSaving_it;
	tmNfo_TimeToReturn.daylightSaving_nl = daylightSaving_nl;
	tmNfo_TimeToReturn.daylightSaving_no = daylightSaving_no;
	tmNfo_TimeToReturn.daylightSaving_jp = daylightSaving_jp;
	tmNfo_TimeToReturn.daylightSaving_pt = daylightSaving_pt;
	tmNfo_TimeToReturn.daylightSaving_ru = daylightSaving_ru;
	tmNfo_TimeToReturn.daylightSaving_sp = daylightSaving_sp;
		
	return tmNfo_TimeToReturn ;
}


int main()
{
	timeinfo_t tmNfo_MyTime = GetTime();
	    
	std::cout << "&#36039;&#26009;: " << tmNfo_MyTime.weekDay_cn << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_cn << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_de << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_de << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_en << ", " << tmNfo_MyTime.month << "/" << tmNfo_MyTime.day << "/" << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_en << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_fr << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_fr << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_it << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_it << "\n";
	std::cout << "&#26085;&#20184;: " << tmNfo_MyTime.weekDay_jp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_jp << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_nl << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_nl << "\n";
	std::cout << "Dato: " << tmNfo_MyTime.weekDay_no << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_no << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_pt << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_pt << "\n";
	std::cout << "&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_ru << "\n";
	std::wcout << L"&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << L", "<< tmNfo_MyTime.day << L"." << tmNfo_MyTime.month << L"." << tmNfo_MyTime.year << L", " << tmNfo_MyTime.hours << L":" << tmNfo_MyTime.minutes << L":" << tmNfo_MyTime.seconds << L" "<< tmNfo_MyTime.daylightSaving_ru << L"\n";
	std::cout << "Fecha: " << tmNfo_MyTime.weekDay_sp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_sp << "\n";
	
	std::cout << "&#36889;&#26159;&#24180;&#30340;&#31532; " << tmNfo_MyTime.dayInYear << ". &#22825;&#12290;" << std::endl ; // not correct for first   //cn
	std::cout << "Dies ist der " << tmNfo_MyTime.dayInYear << ". Tag im Jahr." << std::endl ; // always correct // de
	std::cout << "This is the " << tmNfo_MyTime.dayInYear << "th day in the year." << std::endl ; // not correct for 1st, 2nd, 3rd, and derivatives //en
	std::cout << "C'est le " << tmNfo_MyTime.dayInYear << "ième jour dans l'année." << std::endl ; // not correct for ier //fr
	std::cout << "Questo è il " << tmNfo_MyTime.dayInYear << " giorno nell'anno." << std::endl ; // don't know Italian // it
	std::cout << "&#12371;&#12428;&#12399; " << tmNfo_MyTime.dayInYear << " &#26085;&#30446;&#12395;&#12381;&#12398;&#24180;&#12395;&#12391;&#12377;&#12290;" << std::endl ; // don't know Japanese, but looks like it's always correct // jp
	std::cout << "Dit is de " << tmNfo_MyTime.dayInYear << ". dag in het jaar." << std::endl ; // don't know Dutch, but probably like German // nl
	std::cout << "Dette er " << tmNfo_MyTime.dayInYear << ". dagen i året." << std::endl ; // don't know Norwegian // no
	std::cout << "Isto é o " << tmNfo_MyTime.dayInYear << ". dia o ano." << std::endl ; // don't know Portugues // pt
	std::cout << "&#1069;&#1090;&#1086; " << tmNfo_MyTime.dayInYear << ". &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;." << std::endl ; // always correct // ru
	std::cout << "Este es el " << tmNfo_MyTime.dayInYear << ". día en el año." << std::endl ; // don't know Spanish // sp
}

// ----------------------------------------------

// Fields of the tm struct (C++ syntax):
/*
   struct tm
   {
       int tm_sec;   // seconds after minute 0..60
       int tm_min;   // minutes after hour 0..59
       int tm_hour;  // hours since midnight 0..23
       int tm_mday;  // day of month 1..31
       int tm_mon;   // months since January 0..11
       int tm_year;  // years since 1900
       int tm_wday;  // days since Sunday 0..6
       int tm_yday;  // days since January 1 0..365
       int tm_isdst; // Daylight Saving Time flag
   };
*/

// Declarations for gmtime and localtime functions (C++ syntax):

// tm *localtime(const time_t * timer);
// tm *gmtime(const time_t * timer);

```

---

### Post by quandary on 2008-01-12
Oh, got it working now. 
I woundered why it prints Chinese characters correctly, while not using Unicode, so i just tried not using Unicode.
... and somehow it now works without even using Unicode.
It didn't before...

Does g++ somehow determine a file's encoding, and use Unicode automatically, therefore going mad when I use Unicode types ?


Here the code for what is now working:
```

#include <iostream>
#include <ctime>


struct timeinfo_t
{
	int day ;
	int month ;
	int year ;
	int hours ;
	int minutes ;
	int seconds ;
	int weekDayNumber ;
	int dayInYear ;
	int daylightSavingTime ;
	
	char* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	char* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	char* weekDay_ru ;
    char* weekDay_sp ;
    
	char* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	char* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	char* daylightSaving_ru;
	char* daylightSaving_sp;
};

timeinfo_t GetTime()
{
	time_t sysTime ;
	tm *tmptr_CurrentTime ;
	sysTime = time(NULL) ;
	tmptr_CurrentTime = localtime(&sysTime) ; // for localized time
	//tmptr_CurrentTime = gmtime(&sysTime) ; // for GMT
	
	// Convert
	int weekDayNumber = tmptr_CurrentTime->tm_wday ;  // days since Sunday 0..6
	int daylightSavingTime = tmptr_CurrentTime->tm_isdst ; // Daylight Saving Time flag, 0 = winterTime, 1 = summerTime; 
	// GMT has no Daylight Saving Time
	
	char* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	char* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	char* weekDay_ru ;
	char* weekDay_sp ;
	
	char* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	char* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	char* daylightSaving_ru;
	char* daylightSaving_sp;
	
	if (daylightSavingTime) // 1 for summer time, at least for CET
	{
		daylightSaving_cn= "(&#20013;&#27472;&#22799;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#22799;&#22825;&#26178;&#38291;
		daylightSaving_de="(MESZ)" ; // Mitteleuropäische Sommerzeit
		daylightSaving_en="(CEST)" ; // Central European Summer Time
		daylightSaving_fr="(HECE)" ; // Heure d'Europe centrale d&#8217;été
		daylightSaving_it="(OLFEC)" ; // Ora legale fuso dell'Europa Centrale  
		daylightSaving_jp= "(&#20013;&#12520;&#22799;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#22799;&#26178;
		daylightSaving_no="(MEST)" ; // Mellom-europeisk Sommertid
		daylightSaving_nl="(CEZT)" ; // Centrale Europese zomertijd
		daylightSaving_pt="(HECV)" ; // Hora da Europa Central de verão 
		daylightSaving_ru= "(&#1062;&#1045;&#1051;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1083;&#1077;&#1090;&#1085;&#1077;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HECV)" ; // Hora del Europa Central de verano
	}
	else
	{
		daylightSaving_cn= "(&#20013;&#27472;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#26178;&#38291;
		daylightSaving_de="(MEZ)" ; // Mitteleuropäische Zeit
		daylightSaving_en="(CET)" ; // Central European Time
		daylightSaving_fr="(HEC)" ; // Heure d'Europe centrale
		daylightSaving_it="(FOEC)" ; // Fuso orario dell'Europa Centrale 
		daylightSaving_jp= "(&#20013;&#12520;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#26178;
		daylightSaving_no="(MET)" ; // Mellom-europeisk Tid
		daylightSaving_nl="(CET)" ; // Centrale Europese Tijd
		daylightSaving_pt="(HEC)" ; // Hora da Europa Central 
		daylightSaving_ru= "(&#1062;&#1045;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HEC)" ; // Hora del Europa Central
	}
	
	switch (weekDayNumber) // 0: Sunday, 1: Monday, 2: Tuesday, 3: Wednesday, 4: Thursday, 5: Friday, 6: Saturday
	{
		case 0:
			weekDay_cn = "&#26143;&#26399;&#22825;" ;
			weekDay_de = "Sonntag" ;
			weekDay_en = "Sunday" ;  // should have used Lord's day ;-)
			weekDay_fr = "Dimanche" ;
			weekDay_it = "Domenica" ;
			weekDay_jp = "&#26085;&#26332;&#26085;" ;
			weekDay_nl = "Zondag" ;
			weekDay_no = "Søndag" ;
			weekDay_pt = "Domingo" ;
			weekDay_ru = "&#1042;&#1086;&#1089;&#1082;&#1088;&#1077;&#1089;&#1077;&#1085;&#1100;&#1077;" ;
			weekDay_sp = "Domingo" ;
			break;
		
		case 1: 
			weekDay_cn = "&#26143;&#26399;&#19968;" ;
			weekDay_de = "Montag" ;
			weekDay_en = "Monday" ;
			weekDay_fr = "Lundi" ;
			weekDay_it = "Lunedì" ;
			weekDay_jp = "&#26376;&#26332;&#26085;" ;
			weekDay_nl = "Maandag" ;
			weekDay_no = "Mandag" ;
			weekDay_pt = "Segunda-feira" ;
			weekDay_ru = "&#1055;&#1086;&#1085;&#1077;&#1076;&#1077;&#1083;&#1100;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Lunes" ;
			break;
		
		case 2:
			weekDay_cn = "&#26143;&#26399;&#20108;" ;
			weekDay_de = "Dienstag" ;
			weekDay_en = "Tuesday" ;
			weekDay_fr = "Mardi" ;
			weekDay_it = "Martedì" ;
			weekDay_jp = "&#28779;&#26332;&#26085;" ;
			weekDay_nl = "Dinsdag" ;
			weekDay_no = "Tirsdag" ;
			weekDay_pt = "Terça-feira" ;
			weekDay_ru = "&#1042;&#1090;&#1086;&#1088;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Martes" ;
			break;
		
		case 3:
			weekDay_cn = "&#26143;&#26399;&#19977;" ;
			weekDay_de = "Mittwoch" ;
			weekDay_en = "Wednesday" ;
			weekDay_fr = "Mercredi" ;
			weekDay_it = "Mercoledì" ;
			weekDay_jp = "&#27700;&#26332;&#26085;" ;
			weekDay_nl = "Woensdag" ;
			weekDay_no = "Onsdag" ;
			weekDay_pt = "Quarta-feira" ;
			weekDay_ru = "&#1057;&#1088;&#1077;&#1076;&#1072;" ;
			weekDay_sp = "Miércoles" ;
			break;
		
		case 4:
			weekDay_cn = "&#26143;&#26399;&#22235;" ;
			weekDay_de = "Donnerstag" ;
			weekDay_en = "Thursday" ;
			weekDay_fr = "Jeudi" ;
			weekDay_it = "Giovedì" ;
			weekDay_jp = "&#26408;&#26332;&#26085;" ;
			weekDay_nl = "Donderdag" ;
			weekDay_no = "Torsdag" ;
			weekDay_pt = "Quinta-feira" ;
			weekDay_ru = "&#1063;&#1077;&#1090;&#1074;&#1077;&#1088;&#1075;" ;
			weekDay_sp = "Jueves" ;
			break;
		
		case 5:
			weekDay_cn = "&#26143;&#26399;&#20116;" ;
			weekDay_de = "Freitag" ;
			weekDay_en = "Friday" ;
			weekDay_fr = "Vendredi" ;
			weekDay_it = "Venerdì" ;
			weekDay_jp = "&#37329;&#26332;&#26085;" ;
			weekDay_nl = "Vrijdag" ;
			weekDay_no = "Fredag" ;
			weekDay_pt = "Sexta-feira" ;
			weekDay_ru = "&#1055;&#1103;&#1090;&#1085;&#1080;&#1094;&#1072;" ;
			weekDay_sp = "Viernes" ;
			break;
		
		case 6:
			weekDay_cn = "&#26143;&#26399;&#20845;" ;
			weekDay_de = "Samstag" ;
			weekDay_en = "Saturday" ;
			weekDay_fr = "Samedi" ;
			weekDay_it = "Sabato" ;
			weekDay_jp = "&#22303;&#26332;&#26085;&#12395;" ;
			weekDay_nl = "Zaterdag" ;
			weekDay_no = "Lørdag" ;
			weekDay_pt = "Sábado" ;
			weekDay_ru = "&#1057;&#1091;&#1073;&#1073;&#1086;&#1090;&#1072;" ;
			weekDay_sp = "Sábado" ;
			break;
		
		default: // do these if expr != any above
			weekDay_cn = "&#37679;&#35492;" ;
			weekDay_de = "Fehler" ;  
			weekDay_en = "Error" ;
			weekDay_fr = "Erreur" ; 
			weekDay_it = "Errore" ;
			weekDay_jp = "&#12456;&#12521;&#12540;&#12308;&#35492;&#12426;&#12309;" ;
			weekDay_nl = "De fout" ;
			weekDay_no = "Feil" ;
			weekDay_pt = "Erro" ;
			weekDay_ru = "&#1044;&#1077;&#1092;&#1077;&#1082;&#1090;" ;
			weekDay_sp = "Error" ;
	}
	// end converting
	
	timeinfo_t tmNfo_TimeToReturn;	
	
	tmNfo_TimeToReturn.day = tmptr_CurrentTime->tm_mday ;
	tmNfo_TimeToReturn.month = 1 + tmptr_CurrentTime->tm_mon ;
	tmNfo_TimeToReturn.year = 1900 + tmptr_CurrentTime->tm_year ;
	tmNfo_TimeToReturn.hours = tmptr_CurrentTime->tm_hour ;
	tmNfo_TimeToReturn.minutes = tmptr_CurrentTime->tm_min ;
	tmNfo_TimeToReturn.seconds = tmptr_CurrentTime->tm_sec ;
	tmNfo_TimeToReturn.weekDayNumber = weekDayNumber ;
	tmNfo_TimeToReturn.dayInYear = 1 + tmptr_CurrentTime->tm_yday ;  // days since January 1,  0..365 // probably 364
	tmNfo_TimeToReturn.daylightSavingTime = daylightSavingTime ;
	
	tmNfo_TimeToReturn.weekDay_cn = weekDay_cn ;
	tmNfo_TimeToReturn.weekDay_de = weekDay_de ;
	tmNfo_TimeToReturn.weekDay_en = weekDay_en ;
	tmNfo_TimeToReturn.weekDay_fr = weekDay_fr ;
	tmNfo_TimeToReturn.weekDay_it = weekDay_it ;
	tmNfo_TimeToReturn.weekDay_jp = weekDay_jp ;
	tmNfo_TimeToReturn.weekDay_nl = weekDay_nl ;
	tmNfo_TimeToReturn.weekDay_no = weekDay_no ;
	tmNfo_TimeToReturn.weekDay_pt = weekDay_pt ;
	tmNfo_TimeToReturn.weekDay_ru = weekDay_ru ;
	tmNfo_TimeToReturn.weekDay_sp = weekDay_sp ;
	
	tmNfo_TimeToReturn.daylightSaving_cn = daylightSaving_cn;
	tmNfo_TimeToReturn.daylightSaving_de = daylightSaving_de;
	tmNfo_TimeToReturn.daylightSaving_en = daylightSaving_en;
	tmNfo_TimeToReturn.daylightSaving_fr = daylightSaving_fr;
	tmNfo_TimeToReturn.daylightSaving_it = daylightSaving_it;
	tmNfo_TimeToReturn.daylightSaving_nl = daylightSaving_nl;
	tmNfo_TimeToReturn.daylightSaving_no = daylightSaving_no;
	tmNfo_TimeToReturn.daylightSaving_jp = daylightSaving_jp;
	tmNfo_TimeToReturn.daylightSaving_pt = daylightSaving_pt;
	tmNfo_TimeToReturn.daylightSaving_ru = daylightSaving_ru;
	tmNfo_TimeToReturn.daylightSaving_sp = daylightSaving_sp;
		
	return tmNfo_TimeToReturn ;
}


int main()
{
	timeinfo_t tmNfo_MyTime = GetTime();
	    
	std::cout << "&#36039;&#26009;: " << tmNfo_MyTime.weekDay_cn << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_cn << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_de << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_de << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_en << ", " << tmNfo_MyTime.month << "/" << tmNfo_MyTime.day << "/" << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_en << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_fr << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_fr << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_it << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_it << "\n";
	std::cout << "&#26085;&#20184;: " << tmNfo_MyTime.weekDay_jp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_jp << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_nl << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_nl << "\n";
	std::cout << "Dato: " << tmNfo_MyTime.weekDay_no << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_no << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_pt << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_pt << "\n";
	std::cout << "&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_ru << "\n";
	std::cout << "Fecha: " << tmNfo_MyTime.weekDay_sp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_sp << "\n";
	
	std::cout << "&#36889;&#26159;&#24180;&#30340;&#31532; " << tmNfo_MyTime.dayInYear << ". &#22825;&#12290;" << std::endl ; // not correct for first   //cn
	std::cout << "Dies ist der " << tmNfo_MyTime.dayInYear << ". Tag im Jahr." << std::endl ; // always correct // de
	std::cout << "This is the " << tmNfo_MyTime.dayInYear << "th day in the year." << std::endl ; // not correct for 1st, 2nd, 3rd, and derivatives //en
	std::cout << "C'est le " << tmNfo_MyTime.dayInYear << "ième jour dans l'année." << std::endl ; // not correct for ier //fr
	std::cout << "Questo è il " << tmNfo_MyTime.dayInYear << " giorno nell'anno." << std::endl ; // don't know Italian // it
	std::cout << "&#12371;&#12428;&#12399; " << tmNfo_MyTime.dayInYear << " &#26085;&#30446;&#12395;&#12381;&#12398;&#24180;&#12395;&#12391;&#12377;&#12290;" << std::endl ; // don't know Japanese, but looks like it's always correct // jp
	std::cout << "Dit is de " << tmNfo_MyTime.dayInYear << ". dag in het jaar." << std::endl ; // don't know Dutch, but probably like German // nl
	std::cout << "Dette er " << tmNfo_MyTime.dayInYear << ". dagen i året." << std::endl ; // don't know Norwegian // no
	std::cout << "Isto é o " << tmNfo_MyTime.dayInYear << ". dia o ano." << std::endl ; // don't know Portugues // pt
	std::cout << "&#1069;&#1090;&#1086; " << tmNfo_MyTime.dayInYear << ". &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;." << std::endl ; // always correct // ru
	std::cout << "Este es el " << tmNfo_MyTime.dayInYear << ". día en el año." << std::endl ; // don't know Spanish // sp
}

// ----------------------------------------------

// Fields of the tm struct (C++ syntax):
/*
   struct tm
   {
       int tm_sec;   // seconds after minute 0..60
       int tm_min;   // minutes after hour 0..59
       int tm_hour;  // hours since midnight 0..23
       int tm_mday;  // day of month 1..31
       int tm_mon;   // months since January 0..11
       int tm_year;  // years since 1900
       int tm_wday;  // days since Sunday 0..6
       int tm_yday;  // days since January 1 0..365
       int tm_isdst; // Daylight Saving Time flag
   };
*/

// Declarations for gmtime and localtime functions (C++ syntax):

// tm *localtime(const time_t * timer);
// tm *gmtime(const time_t * timer);

```

---

### Post by quandary on 2008-01-12
Final version:

If the local time zone has the same daylightsaving-flag as CET, then this works, else not.

```

#include <iostream>
#include <ctime>


struct timeinfo_t
{
	int day ;
	int month ;
	int year ;
	int hours ;
	int minutes ;
	int seconds ;
	int weekDayNumber ;
	int dayInYear ;
	int daylightSavingTime ;
	
	char* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	char* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	char* weekDay_ru ;
    char* weekDay_sp ;
    
	char* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	char* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	char* daylightSaving_ru;
	char* daylightSaving_sp;
};

timeinfo_t GetTime()
{
	time_t sysTime ;
	tm *tmptr_CurrentTime ;
	sysTime = time(NULL) ;
	tmptr_CurrentTime = localtime(&sysTime) ; // for localized time
	
	char* weekDay_cn ;
	char* weekDay_de ;
	char* weekDay_en ;
	char* weekDay_fr ;
	char* weekDay_it ;
	char* weekDay_jp ;
	char* weekDay_nl ;
	char* weekDay_no ;
	char* weekDay_pt ;
	char* weekDay_ru ;
	char* weekDay_sp ;
	
	char* daylightSaving_cn;
	char* daylightSaving_de;
	char* daylightSaving_en;
	char* daylightSaving_fr;
	char* daylightSaving_it;
	char* daylightSaving_jp;
	char* daylightSaving_nl;
	char* daylightSaving_no;
	char* daylightSaving_pt;
	char* daylightSaving_ru;
	char* daylightSaving_sp;
	
	// Convert
	int daylightSavingTime = tmptr_CurrentTime->tm_isdst ; // Daylight Saving Time flag, 0 = winterTime, 1 = summerTime; 
	
	if (daylightSavingTime) // 1 for summer time, at least for CET
	{
		daylightSaving_cn= "(&#20013;&#27472;&#22799;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#22799;&#22825;&#26178;&#38291;
		daylightSaving_de="(MESZ)" ; // Mitteleuropäische Sommerzeit
		daylightSaving_en="(CEST)" ; // Central European Summer Time
		daylightSaving_fr="(HECE)" ; // Heure d'Europe centrale d&#8217;été
		daylightSaving_it="(OLFEC)" ; // Ora legale fuso dell'Europa Centrale  
		daylightSaving_jp= "(&#20013;&#12520;&#22799;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#22799;&#26178;
		daylightSaving_no="(MEST)" ; // Mellom-europeisk Sommertid
		daylightSaving_nl="(CEZT)" ; // Centrale Europese zomertijd
		daylightSaving_pt="(HECV)" ; // Hora da Europa Central de verão 
		daylightSaving_ru= "(&#1062;&#1045;&#1051;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1083;&#1077;&#1090;&#1085;&#1077;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HECV)" ; // Hora del Europa Central de verano
	}
	else
	{
		daylightSaving_cn= "(&#20013;&#27472;&#26178;)" ; // &#20013;&#22830;&#27472;&#27954;&#30340;&#26178;&#38291;
		daylightSaving_de="(MEZ)" ; // Mitteleuropäische Zeit
		daylightSaving_en="(CET)" ; // Central European Time
		daylightSaving_fr="(HEC)" ; // Heure d'Europe centrale
		daylightSaving_it="(FOEC)" ; // Fuso orario dell'Europa Centrale 
		daylightSaving_jp= "(&#20013;&#12520;&#26178;)" ; // &#20013;&#22830;&#12520;&#12540;&#12525;&#12483;&#12497;&#27161;&#28310;&#26178;
		daylightSaving_no="(MET)" ; // Mellom-europeisk Tid
		daylightSaving_nl="(CET)" ; // Centrale Europese Tijd
		daylightSaving_pt="(HEC)" ; // Hora da Europa Central 
		daylightSaving_ru= "(&#1062;&#1045;&#1042;)" ; // &#1062;&#1077;&#1085;&#1090;&#1088;&#1072;&#1083;&#1100;&#1085;&#1086;&#1077;&#1074;&#1088;&#1086;&#1087;&#1077;&#1081;&#1089;&#1082;&#1086;&#1077; &#1074;&#1088;&#1077;&#1084;&#1103; 
		daylightSaving_sp="(HEC)" ; // Hora del Europa Central
	}
	
	tmptr_CurrentTime = gmtime(&sysTime) ; // now using GMT
	// GMT has no Daylight Saving Time, so i had to initialize with localtime first
	
	int weekDayNumber = tmptr_CurrentTime->tm_wday ;  // days since Sunday 0..6
	
	switch (weekDayNumber) // 0: Sunday, 1: Monday, 2: Tuesday, 3: Wednesday, 4: Thursday, 5: Friday, 6: Saturday
	{
		case 0:
			weekDay_cn = "&#26143;&#26399;&#22825;" ;
			weekDay_de = "Sonntag" ;
			weekDay_en = "Sunday" ;  // should have used Lord's day ;-)
			weekDay_fr = "Dimanche" ;
			weekDay_it = "Domenica" ;
			weekDay_jp = "&#26085;&#26332;&#26085;" ;
			weekDay_nl = "Zondag" ;
			weekDay_no = "Søndag" ;
			weekDay_pt = "Domingo" ;
			weekDay_ru = "&#1042;&#1086;&#1089;&#1082;&#1088;&#1077;&#1089;&#1077;&#1085;&#1100;&#1077;" ;
			weekDay_sp = "Domingo" ;
			break;
		
		case 1: 
			weekDay_cn = "&#26143;&#26399;&#19968;" ;
			weekDay_de = "Montag" ;
			weekDay_en = "Monday" ;
			weekDay_fr = "Lundi" ;
			weekDay_it = "Lunedì" ;
			weekDay_jp = "&#26376;&#26332;&#26085;" ;
			weekDay_nl = "Maandag" ;
			weekDay_no = "Mandag" ;
			weekDay_pt = "Segunda-feira" ;
			weekDay_ru = "&#1055;&#1086;&#1085;&#1077;&#1076;&#1077;&#1083;&#1100;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Lunes" ;
			break;
		
		case 2:
			weekDay_cn = "&#26143;&#26399;&#20108;" ;
			weekDay_de = "Dienstag" ;
			weekDay_en = "Tuesday" ;
			weekDay_fr = "Mardi" ;
			weekDay_it = "Martedì" ;
			weekDay_jp = "&#28779;&#26332;&#26085;" ;
			weekDay_nl = "Dinsdag" ;
			weekDay_no = "Tirsdag" ;
			weekDay_pt = "Terça-feira" ;
			weekDay_ru = "&#1042;&#1090;&#1086;&#1088;&#1085;&#1080;&#1082;" ;
			weekDay_sp = "Martes" ;
			break;
		
		case 3:
			weekDay_cn = "&#26143;&#26399;&#19977;" ;
			weekDay_de = "Mittwoch" ;
			weekDay_en = "Wednesday" ;
			weekDay_fr = "Mercredi" ;
			weekDay_it = "Mercoledì" ;
			weekDay_jp = "&#27700;&#26332;&#26085;" ;
			weekDay_nl = "Woensdag" ;
			weekDay_no = "Onsdag" ;
			weekDay_pt = "Quarta-feira" ;
			weekDay_ru = "&#1057;&#1088;&#1077;&#1076;&#1072;" ;
			weekDay_sp = "Miércoles" ;
			break;
		
		case 4:
			weekDay_cn = "&#26143;&#26399;&#22235;" ;
			weekDay_de = "Donnerstag" ;
			weekDay_en = "Thursday" ;
			weekDay_fr = "Jeudi" ;
			weekDay_it = "Giovedì" ;
			weekDay_jp = "&#26408;&#26332;&#26085;" ;
			weekDay_nl = "Donderdag" ;
			weekDay_no = "Torsdag" ;
			weekDay_pt = "Quinta-feira" ;
			weekDay_ru = "&#1063;&#1077;&#1090;&#1074;&#1077;&#1088;&#1075;" ;
			weekDay_sp = "Jueves" ;
			break;
		
		case 5:
			weekDay_cn = "&#26143;&#26399;&#20116;" ;
			weekDay_de = "Freitag" ;
			weekDay_en = "Friday" ;
			weekDay_fr = "Vendredi" ;
			weekDay_it = "Venerdì" ;
			weekDay_jp = "&#37329;&#26332;&#26085;" ;
			weekDay_nl = "Vrijdag" ;
			weekDay_no = "Fredag" ;
			weekDay_pt = "Sexta-feira" ;
			weekDay_ru = "&#1055;&#1103;&#1090;&#1085;&#1080;&#1094;&#1072;" ;
			weekDay_sp = "Viernes" ;
			break;
		
		case 6:
			weekDay_cn = "&#26143;&#26399;&#20845;" ;
			weekDay_de = "Samstag" ;
			weekDay_en = "Saturday" ;
			weekDay_fr = "Samedi" ;
			weekDay_it = "Sabato" ;
			weekDay_jp = "&#22303;&#26332;&#26085;&#12395;" ;
			weekDay_nl = "Zaterdag" ;
			weekDay_no = "Lørdag" ;
			weekDay_pt = "Sábado" ;
			weekDay_ru = "&#1057;&#1091;&#1073;&#1073;&#1086;&#1090;&#1072;" ;
			weekDay_sp = "Sábado" ;
			break;
		
		default: // do these if expr != any above
			weekDay_cn = "&#37679;&#35492;" ;
			weekDay_de = "Fehler" ;  
			weekDay_en = "Error" ;
			weekDay_fr = "Erreur" ; 
			weekDay_it = "Errore" ;
			weekDay_jp = "&#12456;&#12521;&#12540;&#12308;&#35492;&#12426;&#12309;" ;
			weekDay_nl = "De fout" ;
			weekDay_no = "Feil" ;
			weekDay_pt = "Erro" ;
			weekDay_ru = "&#1044;&#1077;&#1092;&#1077;&#1082;&#1090;" ;
			weekDay_sp = "Error" ;
	}
	// end converting
	
	timeinfo_t tmNfo_TimeToReturn;	
	
	tmNfo_TimeToReturn.day = tmptr_CurrentTime->tm_mday ;
	tmNfo_TimeToReturn.month = 1 + tmptr_CurrentTime->tm_mon ;
	tmNfo_TimeToReturn.year = 1900 + tmptr_CurrentTime->tm_year ;
	if (daylightSavingTime) // 1 for summer time, at least for CET
		tmNfo_TimeToReturn.hours = 2 + tmptr_CurrentTime->tm_hour ; // GMT2CEST = +2
	else
		tmNfo_TimeToReturn.hours = 1 + tmptr_CurrentTime->tm_hour ; // GMT2CET = +1
	tmNfo_TimeToReturn.minutes = tmptr_CurrentTime->tm_min ;
	tmNfo_TimeToReturn.seconds = tmptr_CurrentTime->tm_sec ;
	tmNfo_TimeToReturn.weekDayNumber = weekDayNumber ;
	tmNfo_TimeToReturn.dayInYear = 1 + tmptr_CurrentTime->tm_yday ;  // days since January 1,  0..365 // probably 364
	tmNfo_TimeToReturn.daylightSavingTime = daylightSavingTime ;
	
	tmNfo_TimeToReturn.weekDay_cn = weekDay_cn ;
	tmNfo_TimeToReturn.weekDay_de = weekDay_de ;
	tmNfo_TimeToReturn.weekDay_en = weekDay_en ;
	tmNfo_TimeToReturn.weekDay_fr = weekDay_fr ;
	tmNfo_TimeToReturn.weekDay_it = weekDay_it ;
	tmNfo_TimeToReturn.weekDay_jp = weekDay_jp ;
	tmNfo_TimeToReturn.weekDay_nl = weekDay_nl ;
	tmNfo_TimeToReturn.weekDay_no = weekDay_no ;
	tmNfo_TimeToReturn.weekDay_pt = weekDay_pt ;
	tmNfo_TimeToReturn.weekDay_ru = weekDay_ru ;
	tmNfo_TimeToReturn.weekDay_sp = weekDay_sp ;
	
	tmNfo_TimeToReturn.daylightSaving_cn = daylightSaving_cn;
	tmNfo_TimeToReturn.daylightSaving_de = daylightSaving_de;
	tmNfo_TimeToReturn.daylightSaving_en = daylightSaving_en;
	tmNfo_TimeToReturn.daylightSaving_fr = daylightSaving_fr;
	tmNfo_TimeToReturn.daylightSaving_it = daylightSaving_it;
	tmNfo_TimeToReturn.daylightSaving_nl = daylightSaving_nl;
	tmNfo_TimeToReturn.daylightSaving_no = daylightSaving_no;
	tmNfo_TimeToReturn.daylightSaving_jp = daylightSaving_jp;
	tmNfo_TimeToReturn.daylightSaving_pt = daylightSaving_pt;
	tmNfo_TimeToReturn.daylightSaving_ru = daylightSaving_ru;
	tmNfo_TimeToReturn.daylightSaving_sp = daylightSaving_sp;
		
	return tmNfo_TimeToReturn ;
}


int main()
{
	timeinfo_t tmNfo_MyTime = GetTime();
	    
	std::cout << "&#36039;&#26009;: " << tmNfo_MyTime.weekDay_cn << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_cn << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_de << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_de << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_en << ", " << tmNfo_MyTime.month << "/" << tmNfo_MyTime.day << "/" << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_en << "\n";
	std::cout << "Date: " << tmNfo_MyTime.weekDay_fr << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_fr << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_it << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_it << "\n";
	std::cout << "&#26085;&#20184;: " << tmNfo_MyTime.weekDay_jp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_jp << "\n";
	std::cout << "Datum: " << tmNfo_MyTime.weekDay_nl << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_nl << "\n";
	std::cout << "Dato: " << tmNfo_MyTime.weekDay_no << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_no << "\n";
	std::cout << "Data: " << tmNfo_MyTime.weekDay_pt << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_pt << "\n";
	std::cout << "&#1076;&#1072;&#1090;&#1072;: " << tmNfo_MyTime.weekDay_ru << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_ru << "\n";
	std::cout << "Fecha: " << tmNfo_MyTime.weekDay_sp << ", "<< tmNfo_MyTime.day << "." << tmNfo_MyTime.month << "." << tmNfo_MyTime.year << ", " << tmNfo_MyTime.hours << ":" << tmNfo_MyTime.minutes << ":" << tmNfo_MyTime.seconds << " "<< tmNfo_MyTime.daylightSaving_sp << "\n";
	
	std::cout << "&#36889;&#26159;&#24180;&#30340;&#31532; " << tmNfo_MyTime.dayInYear << ". &#22825;&#12290;" << std::endl ; // not correct for first   //cn
	std::cout << "Dies ist der " << tmNfo_MyTime.dayInYear << ". Tag im Jahr." << std::endl ; // always correct // de
	std::cout << "This is the " << tmNfo_MyTime.dayInYear << "th day in the year." << std::endl ; // not correct for 1st, 2nd, 3rd, and derivatives //en
	std::cout << "C'est le " << tmNfo_MyTime.dayInYear << "ième jour dans l'année." << std::endl ; // not correct for ier //fr
	std::cout << "Questo è il " << tmNfo_MyTime.dayInYear << " giorno nell'anno." << std::endl ; // don't know Italian // it
	std::cout << "&#12371;&#12428;&#12399; " << tmNfo_MyTime.dayInYear << " &#26085;&#30446;&#12395;&#12381;&#12398;&#24180;&#12395;&#12391;&#12377;&#12290;" << std::endl ; // don't know Japanese, but looks like it's always correct // jp
	std::cout << "Dit is de " << tmNfo_MyTime.dayInYear << ". dag in het jaar." << std::endl ; // don't know Dutch, but probably like German // nl
	std::cout << "Dette er " << tmNfo_MyTime.dayInYear << ". dagen i året." << std::endl ; // don't know Norwegian // no
	std::cout << "Isto é o " << tmNfo_MyTime.dayInYear << ". dia o ano." << std::endl ; // don't know Portugues // pt
	std::cout << "&#1069;&#1090;&#1086; " << tmNfo_MyTime.dayInYear << ". &#1076;&#1077;&#1085;&#1100; &#1074; &#1075;&#1086;&#1076;&#1091;." << std::endl ; // always correct // ru
	std::cout << "Este es el " << tmNfo_MyTime.dayInYear << ". día en el año." << std::endl ; // don't know Spanish // sp
}

// ----------------------------------------------

// Fields of the tm struct (C++ syntax):
/*
   struct tm
   {
       int tm_sec;   // seconds after minute 0..60
       int tm_min;   // minutes after hour 0..59
       int tm_hour;  // hours since midnight 0..23
       int tm_mday;  // day of month 1..31
       int tm_mon;   // months since January 0..11
       int tm_year;  // years since 1900
       int tm_wday;  // days since Sunday 0..6
       int tm_yday;  // days since January 1 0..365
       int tm_isdst; // Daylight Saving Time flag
   };
*/

// Declarations for gmtime and localtime functions (C++ syntax):

// tm *localtime(const time_t * timer);
// tm *gmtime(const time_t * timer);

```

---

