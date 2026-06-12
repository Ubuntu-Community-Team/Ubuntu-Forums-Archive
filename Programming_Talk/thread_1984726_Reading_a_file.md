---
title: "Reading a file"
date: 2012-05-22
forum: Programming Talk
---

### Post by Markanbl on 2012-05-22
Hi, I have a question about reading a file with C++. I have to read a file of following type

Name
1#00:00#00:00#00:00
2#00:00#00:00#00:00
3#00:00#00:00#00:00
.
.
.
Something

I need to stock the name in a vector, numbers in a vector from 1 to n and "00:00" parts in three different vectors and "something" in a new vector so I could create an object in the end.

For the moment I have the following code but I am not sure is it working because I get a Signal Aborted error, std::bad_alloc to be precise... :/

```
Household* FileHousehold::readHousehold(string line){
    FileDevices fd("/users/localguest/Desktop/Devices.txt");

    stringstream ss(line);
    string str;
    vector<string> name;
    vector<string> constraint;
    vector<string> sID;
    vector<string> sStartHour;
    vector<string> sStartMin;
    vector<string> sEndHour;
    vector<string> sEndMin;
    vector<string> sDurationHour;
    vector<string> sDurationMin;

    vector<DeviceConstraints*> List_Dev_Con;
    vector<GeneralConstraint*> List_Gen_Con;

    getline(ss, str);
        name.push_back(str);
   
    unsigned int i(0);
    while(getline(ss, str)){
        i++;
        getline(ss, str, '#');
        sID.push_back(str);
        getline(ss, str, ':');
        sStartHour.push_back(str);
        getline(ss, str, '#');
        sStartMin.push_back(str);
        getline(ss, str, ':');
        sEndHour.push_back(str);
        getline(ss, str, '#');
        sEndMin.push_back(str);
        getline(ss, str, ':');
        sDurationHour.push_back(str);
        getline(ss, str);
        sDurationMin.push_back(str);
        vector<Device *> tabDev;
        tabDev = fd.read();

         DeviceConstraints *DC;
         DC = new DeviceConstraints(tabDev[atoi(sID[i].c_str())], Time(atoi(sStartHour[i].c_str()), atoi(sStartMin[i].c_str())),
                        Time(atoi(sEndHour[i].c_str()), atoi(sEndMin[i].c_str())), Time(atoi(sDurationHour[i].c_str()), atoi(sDurationMin[i].c_str())));
         List_Dev_Con.push_back(DC);
    }

        while(getline(ss, str));
        constraint.push_back(str);
   
    GeneralConstraint *GC;
    GC = new GeneralConstraint(atoi(constraint[0].c_str()));
    List_Gen_Con.push_back(GC);

    return new Household(name[0], List_Dev_Con, List_Gen_Con);
}
```


How could I solve this problem? I also tried tokenizers but they are char* type and I need a string... :/
Thanks...

---

### Post by dwhitney67 on 2012-05-22
I'm not sure what you are doing here?
```

        vector<Device *> tabDev;
        tabDev = fd.read();

```
tabDev is a local variable within the while-loop; it will be destroyed once the loop exits.  What bearing this has on your application is unknown.

Avoid using atoi(); it is prone to error, especially if the string that is passed to it does NOT contain any numbers.  In such case, atoi() returns 0.  Using std::stringstream instead to get numbers.

Alternatively, consider using Boost's Tokenizer; here's a simple program:
```

#include <boost/tokenizer.hpp>
#include <string>
#include <sstream>
#include <fstream>
#include <iostream>
#include <cstdlib>

int main()
{
    /*
        Name
        1#00:00#00:00#00:00
        2#00:00#00:00#00:00
        3#00:00#00:00#00:00
        Something
    */
    std::fstream file("data.txt", std::ios::in);

    if (file)
    {
        std::string line;

        std::string name;
        std::string something;

        typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
        boost::char_separator<char> sep("#");

        std::getline(file, name);

        std::cout << "Name      = " << name << std::endl;

        while (std::getline(file, line))
        {
            std::stringstream ss(line);
            int num;
            ss >> num;

            if (!ss.fail())
            {
                Tokenizer info(line, sep);
                Tokenizer::iterator it = info.begin();
                ++it;   // skip number
                std::string time1 = *it++;
                std::string time2 = *it++;
                std::string time3 = *it++;

                std::cout << "Num       = " << num << "\n"
                          << "Time1     = " << time1 << "\n"
                          << "Time2     = " << time2 << "\n"
                          << "Time3     = " << time3
                          << std::endl;
            }
            else
            {
                something = line;
                std::cout << "Something = " << something << std::endl;

                break;
            }
        }
    }

    return 0;
}

```

---

