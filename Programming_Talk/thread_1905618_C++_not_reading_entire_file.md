---
title: "C++ not reading entire file"
date: 2012-01-07
forum: Programming Talk
---

### Post by alexmoca on 2012-01-07
Hi everyone!

I am having dificulties trying to read a big .csv file (a few thousand lines). The problem is that the reading suddenly stops after 4000 something lines (typically before 4600) and I can't figure out why. The number of the last line which is reached varies with each run.

You will see there are some lines (after line 4800) which are empty or have the incorrect format, but those are never reached so I doubt they are the problem. 

I attached the file I am trying to read. Basically I take care of the first 5 lines without any problem. Then when I have to read the actual data I need, I can't reach the end of the file. According to Netbeans, the run is always successful "RUN SUCCESSFUL ". 

Here's my code which is trying to read the +6th lines:

```

void FileReader::readStarData(Star* star, istream* stream) {
    string data;
    int i = 5;
    while(std::getline(*stream, data, ',')) {
        StarData sData;
        sData.quarter = strtof(data.c_str(), NULL);
        
        std::getline(*stream, data, ',');
        sData.time = strtod(data.c_str(), NULL);
        
        std::getline(*stream, data, ',');
        sData.brightness = strtod(data.c_str(), NULL);
        
        std::getline(*stream, data, ',');
        sData.error = strtod(data.c_str(), NULL);
        
        i++;
        cout << i << ": ";
        cout << sData.quarter << " ";
        cout << sData.time << " ";
        cout << sData.brightness << " ";
        cout << sData.error << " " << endl;
    }
}

```

where StarData is:

```

struct StarData {
    float quarter;
    double time; //days
    double brightness;
    double error; //error in brightness
};

```

LE: I forgot to add the attachment.

---

### Post by MadCow108 on 2012-01-07
there is no error checking in that code so it just stops when it reaches the differently formated lines at lines 1644, 3245 etc.

you might also want to use the typesafe stream extraction operators instead of the not-typesafe C ones.
e.g. convert the string from getline into a stringstream and use >>
(or always use >>)

---

