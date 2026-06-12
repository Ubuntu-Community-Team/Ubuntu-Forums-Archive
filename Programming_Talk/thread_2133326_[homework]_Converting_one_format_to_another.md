---
title: "[homework] Converting one format to another"
date: 2013-04-07
forum: Programming Talk
---

### Post by mhaggard on 2013-04-07
I am in a c++ class and my group is having a hard time making this  work... It keeps saying that 'fileOne.open' isn't working. We can't seem  to figure out why. Any help would be greatly appreciated. Thank you in  advance. 

```

#include <iostream>
#include <string>
#include <fstream>
#include "convert.hpp"
using namespace std;

int main()
{
    HydraRecord hClientOne;
    HydraRecord hClientTwo;
    HydraRecord hClientThree;
    HydraRecord hClientFour;
    KrebStarRecord kClient;
    ifstream fileOne;
    ifstream fileTwo;
    ifstream fileThree;
    ifstream fileFour;
    ifstream index;
    ofstream outFile;
    int userResponse;
    int numRecords;
    string One;
    string Two;
    string Three;
    string Four;
    
    outFile.open("records.ksrf");
    
    cout << "Welcome to the record transfer system." << endl;
    cout << "======================================="<<endl;
    
    
    index.open("index.txt");
    if(index.is_open() == false){
        cerr << "ERROR: Cannot open input file. Exiting. [index]" << endl;
        return 1;
    }
    
    index >> numRecords;
    index.ignore(256, '\n');
    
    for (int i = 0; i < numRecords; i++){
        index >> One;
        index >> Two;
        index >> Three;
        index >> Four;
        }
        
    fileOne.open(One.c_str());
    if(fileOne.is_open() == false){
        cerr << "ERROR: Cannot open input file 1. Exiting." << endl;
        return 1;
    }
    fileTwo.open(Two.c_str());
    if(fileTwo.is_open() == false){
        cerr << "ERROR: Cannot open input file 2. Exiting." << endl;
        return 1;
    }
    fileThree.open(Three.c_str());
    if(fileThree.is_open() == false){
        cerr << "ERROR: Cannot open input file 3. Exiting." << endl;
        return 1;
    }
    fileFour.open(Four.c_str());
    if(fileFour.is_open() == false){
        cerr << "ERROR: Cannot open input file 4. Exiting." << endl;
        return 1;
    
    }
    
    fileOne >> numRecords;
    for (int i = 0; i < numRecords; i++){
        fileOne >> hClientOne.customerID;
        fileOne >> hClientOne.customerName;
        fileOne >> hClientOne.customerStreetAddress;
        fileOne >> hClientOne.Address[3];
        fileOne >> hClientOne.customerPhoneNumber;
        fileOne >> hClientOne.dateCreated[3];
        fileOne >> hClientOne.checkingBalance;
        fileOne >> hClientOne.savingBalance;
    }
    
    //convertHydraToKrebStar(hClient);
    
    outFile << "<?xml version=""1.0""?>"<<endl;
    outFile    << "<ksrf>"<<endl;
    outFile    << "    <customer>"<< endl;
    outFile    << "        <id>" << kClient.customerID << "</id>"<<endl;
    outFile    << "        <name>" << kClient.customerName << "</name>"<<endl;
    outFile    << "        <address>"<<endl;
    outFile    << "            <street>" << kClient.customerStreetAddress << "</street>"<<endl;
    outFile    << "            <city>" << kClient.customerCity << "</city>"<<endl;
    outFile    << "            <state>" << kClient.customerState << "</state>"<<endl;
    outFile    << "            <zip>" << kClient.customerZip << "</zip>"<<endl;
    outFile    << "        </address>"<<endl;
    outFile    << "        <phone>" << kClient.customerPhoneNumber << "</phone>"<<endl;
    outFile    << "         <date>"<<endl;
    outFile    << "            <year>" << kClient.yearCreated << "</date>"<<endl;
    outFile    << "            <month>" << kClient.monthCreated << "</month>"<<endl;
    outFile    << "             <day>" << kClient.dayCreated << "</day>" << endl;
    outFile    << "        </date>" << endl;
    outFile    << "         <accounts>"<< endl;
    outFile    << "            <checking>" << kClient.checkingBalance << "</checking>" << endl;
    outFile    << "            <savings>" << kClient.savingBalance << "</savings>"<< endl;
    outFile    << "        </accounts>"<< endl;
    outFile    << "    </customer>" << endl;
    outFile    << "=======================================================================";
    
    outFile << "</ksrf>";
    index.close();
    outFile.close();
}
```

---

### Post by mhaggard on 2013-04-07
okay, We have fixed the 'fileOne' problem, but now file four isn't opening... again thank you in advance for any help.

---

### Post by QIII on 2013-04-07
Hello!

Please review the Forum Code of Conduct.

Although we are happy to provide the occasional tip, the forums are not a homework service.

Thanks, 

QIII

Thread closed.

---

