---
title: "[SOLVED] C++ readfile to vector question"
date: 2008-04-26
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-26
Question about the program listed below:

    for (std::vector<IPinfo_t>::const_iterator IPinfo_Iterator = IPintovect_IPinfo.begin(); IPinfo_Iterator != IPintovect_IPinfo.end()-1; ++IPinfo_Iterator)

I need to do: IPintovect_IPinfo.end()-1
and not
IPintovect_IPinfo.end()

Why does it read the last line twice, and why is there data in it, and not blank or a segmentation fault happening ?

```

#include <iostream>
#include <fstream>
#include <vector>
//#include "bigintclass.h"


//#define DATABASE_PATH "C:\\Documents and Settings\\admin\\My Documents\\Visual Studio Projects\\CreateCompareFile\\ip-to-country.csv"
#define DATABASE_PATH "/root/Desktop/muster.txt"


typedef struct
{
    std::string strLowerNumber ;
	std::string strHigherNumber ;
	std::string strCountry ;
} IPinfo_t ;

std::vector<IPinfo_t> IPintovect_IPinfo ;


void ProcTrimDoubleQuotes(std::string &strInputString)
{
    std::string::size_type sze_QuotePosition = strInputString.find_first_of('\"');
    if (sze_QuotePosition != std::string::npos)
    {
        strInputString.erase(sze_QuotePosition, 1);
    }

    sze_QuotePosition = strInputString.find_last_of('\"');
    if (sze_QuotePosition != std::string::npos)
    {
        strInputString.erase(sze_QuotePosition, 1);
    }
}


void ProcUncapitalize(std::string& strCapitalizedString)
{
	int intStringLength = (int) strCapitalizedString.length();
	int intIndex ;
	for(intIndex=1; intIndex < intStringLength; ++intIndex)
	{
		if(strCapitalizedString[intIndex]==' ')
		{
			if((intIndex+1)< intStringLength)
				++intIndex ;
		}
		else
			strCapitalizedString[intIndex] = tolower(strCapitalizedString[intIndex]);
	}
}



int main()
{
	char Buffer[1024];

	std::ifstream afile(DATABASE_PATH);
	//std::fstream afile("C:\\TABLE.txt", std::ios::out | std::ios::in |std::ios::beg);

	if (!afile) // were there any errors on opening?
	{
		printf("Error opening file...\nFile not found.\nIllegal name, or insufficient permissions\n");
		system("pause");
		exit(EXIT_FAILURE);
	}

	//std::string strLookupNumber(chrptr_IPnumber);
	//BigInteger BigIntLookupNumber = String2BigInt(strLookupNumber);


	std::string strLowerNumber ;
	std::string strHigherNumber ;
	std::string strCountry ;
	//BigInteger BigIntLowerNumber ;
	//BigInteger BigIntHigherNumber ;

    IPinfo_t IPinfo ;


	char* chrptr_Country ;
	//bool boCountryNotFound = true;
	char* pch ;
	int i ;

	while (!afile.eof())
	{
		afile.getline(Buffer, sizeof(Buffer));


		pch = strtok (Buffer,",") ;


		for (i = 0; pch != NULL; ++i)
		{
			if (i==0)
				strLowerNumber = pch;
			else
			{
				if (i == 1)
					strHigherNumber = pch;
				else
				{
					if(i==4)
						strCountry= pch;
				}
			}
			pch = strtok (NULL, ",") ;
		}

		ProcTrimDoubleQuotes(strLowerNumber);
		ProcTrimDoubleQuotes(strHigherNumber);
		ProcTrimDoubleQuotes(strCountry);
		ProcUncapitalize(strCountry);

		IPinfo.strLowerNumber = strLowerNumber ;
        IPinfo.strHigherNumber = strHigherNumber ;
        IPinfo.strCountry = strCountry ;
        IPintovect_IPinfo.push_back(IPinfo) ;
    }

    for (std::vector<IPinfo_t>::const_iterator IPinfo_Iterator = IPintovect_IPinfo.begin(); IPinfo_Iterator != IPintovect_IPinfo.end()-1; ++IPinfo_Iterator)
    {
        printf("strLowerNumber = %s\n", IPinfo_Iterator->strLowerNumber.c_str());
        printf("strHigherNumber = %s\n", IPinfo_Iterator->strHigherNumber.c_str());
        printf("strCountry = %s\n", IPinfo_Iterator->strCountry.c_str());
    }

    return EXIT_SUCCESS ;
}

```

With muster.txt
```

"33996344","33996351","GB","GBR","UNITED KINGDOM"
"50331648","69956103","US","USA","UNITED STATES"
"69956104","69956111","BM","BMU","BERMUDA"
"69956112","83886079","US","USA","UNITED STATES"
"94585424","94585439","SE","SWE","SWEDEN"
"100663296","121195295","US","USA","UNITED STATES"
"121195296","121195327","IT","ITA","ITALY"
"121195328","152305663","US","USA","UNITED STATES"
"152305664","152338431","GB","GBR","UNITED KINGDOM"
"152338432","167772159","US","USA","UNITED STATES"
"184549376","201620303","US","USA","UNITED STATES"
"201620304","201620311","CA","CAN","CANADA"
"201620312","201674095","US","USA","UNITED STATES"
"201674096","201674111","CA","CAN","CANADA"
"201674112","201859071","US","USA","UNITED STATES"
"201859072","201859087","VI","VIR","VIRGIN ISLANDS, U.S."
"201859088","201897983","US","USA","UNITED STATES"
"201897984","201898239","PR","PRI","PUERTO RICO"
"201898240","202035199","US","USA","UNITED STATES"
"202035200","202035711","IN","IND","INDIA"
"202035712","202385407","US","USA","UNITED STATES"
"202385408","202385919","PR","PRI","PUERTO RICO"
"202385920","202706431","US","USA","UNITED STATES"
"202706432","202706943","PR","PRI","PUERTO RICO"
"202706944","202934671","US","USA","UNITED STATES"
"202934672","202934687","VI","VIR","VIRGIN ISLANDS, U.S."
"202934688","202938479","US","USA","UNITED STATES"
"202938480","202938495","VI","VIR","VIRGIN ISLANDS, U.S."
"202938496","203197063","US","USA","UNITED STATES"
"203197064","203197071","CA","CAN","CANADA"
"203197072","203658751","US","USA","UNITED STATES"
"203658752","203658815","VI","VIR","VIRGIN ISLANDS, U.S."
"203658816","203658879","PR","PRI","PUERTO RICO"

```

---

### Post by dwhitney67 on 2008-04-26
I'm not sure what you are asking?

One thing you need to concern yourself with is understanding when the EOF bit is set when reading the file.  It will not be set until a read is performed on the file, and no data remains.

Thus you really should try to combine the getline() and the eof() test within the same while-conditional.  For instance:
[PHP]...
while (afile.getline(Buffer, sizeof Buffer) && !afile.eof())
{
  ...
}[/PHP]

Change your code with the suggestion above, and that will obviate the need to loop until end()-1 in the for-loop.

P.S.  I highly recommend that you typedef your vector definition and it's const iterator.  It makes the code much easier to read.  For example:
[PHP]typedef std::vector<int>      MyVec;
typedef MyVec::const_iterator MyVecIter;
...
MyVec vec;
...
for (MyVecIter it = vec.begin(); it != vec.end; ++it)
{
...
}[/PHP]

---

### Post by Lux Perpetua on 2008-04-26
The idiom I prefer is
```
...
while (afile.getline(Buffer, sizeof Buffer))
{
  ...
}
```I don't recall ever needing to check eof() explicitly.

---

### Post by dwhitney67 on 2008-04-26
Up 2 you.  But if you never check eof explicitly, then why did you do so in the original code you posted?

---

### Post by WitchCraft on 2008-04-27
> **dwhitney67 said:**
> 
Up 2 you.  But if you never check eof explicitly, then why did you do so in the original code you posted?


That in the last post wasn't me, that was "Lux Perpetua". FYI ;-)

Well, thanks, I note that I have to check getline instead of EOF.
And I'll do as you recommend with the typedefs.

Again: Many thanks anyway!

---

