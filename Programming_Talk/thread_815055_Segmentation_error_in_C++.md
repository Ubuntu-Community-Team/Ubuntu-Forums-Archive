---
title: "Segmentation error in C++"
date: 2008-06-01
forum: Programming Talk
---

### Post by arseniy on 2008-06-01
I'm just having some fun with C++ and decided to make a partition editor (not real of course, just a fun fake one) lol.

For some reason, I'm getting a segmentation error. Not only do I NOT know what that means haha, but idk how/where to fix it. Can someone look at the code?

Here's the header file that's causing the problem:

```
#ifndef PARTITION_H_INCLUDED
#define PARTITION_H_INCLUDED
#include <iostream.h>

using namespace std;

typedef enum format {bfs, ext2, ext2cow, ext3, fat, fat32, hfs, hfsplus, jfs, ntfs, ufs2, zfs, emptyspace};

class Partition {
    private:
        format partitionFormat;
        double partitionSize;
    public:
        void setFormat(format);
        void setSize(double);
        format getFormat();
        string getFormatString();
        double getSize();
};

void Partition::setFormat(format desiredFormat) {
    partitionFormat = desiredFormat;
}

void Partition::setSize(double desiredSize) {
    partitionSize = desiredSize;
}

format Partition::getFormat() {
    return partitionFormat;
}

string Partition::getFormatString() {
    string tmp;
    switch (partitionFormat) {
        case 0:
            tmp = "BFS";
            break;
        case 1:
            tmp = "ext2";
            break;
        case 2:
            tmp = "ext3";
            break;
        case 3:
            tmp = "ext3 cow";
            break;
        case 4:
            tmp = "FAT";
            break;
        case 5:
            tmp = "FAT32";
            break;
        case 6:
            tmp = "HFS";
            break;
        case 7:
            tmp = "HFS+";
            break;
        case 8:
            tmp = "JFS";
            break;
        case 9:
            tmp = "NTFS";
            break;
        case 10:
            tmp = "UFS2";
            break;
        case 11:
            tmp = "ZFS";
            break;
        case 12:
            tmp = "empty space";
            break;
    }

    return tmp;
}

double Partition::getSize() {
    return partitionSize;
}

class PartitionMap {
    private:
        int partitionCount;
        Partition initialPartition;
        Partition partitions[];
        void combineByDefault();
    public:
        void setInitialPartition(format, double);
        void insertInitIntoPartitionMap();
        void printInfo();
        void printTechnicalInfo();
        void deletePartition(int);
};

void PartitionMap::setInitialPartition(format desiredFormat, double desiredSize) {
    initialPartition.setFormat(desiredFormat);
    initialPartition.setSize(desiredSize);
    partitionCount = 1;
}

void PartitionMap::insertInitIntoPartitionMap() {
    partitions[0].setFormat(initialPartition.getFormat());
    partitions[0].setSize(initialPartition.getSize());
}

void PartitionMap::combineByDefault() {
    bool partitionDelete[partitionCount];
    bool end = false;

    while (!end) {
        for (int i = 0; i < (partitionCount - 1); i++) {
            if (partitions[i].getFormat() == emptyspace && partitions[i].getFormat() == partitions[i + 1].getFormat()) {
                partitions[i].setSize(partitions[i].getSize() + partitions[i + 1].getSize());
                partitionDelete[i + 1] = true;
            }
        }

        for (int i = 0; i < partitionCount; i++) {
            if (partitionDelete[i] == true) {
                Partition* tmp = &partitions[i];
                delete &tmp;
                delete tmp;
                partitionCount--;
            }
        }

        end = true;

        for (int i = 0; i < (partitionCount - 1); i++) {
            if (partitions[i].getFormat() == emptyspace && partitions[i].getFormat() == partitions[i + 1].getFormat()) {
                end = false;
            }
        }
    }

    cout << "Empty space was combined by default." << endl << endl;
}

void PartitionMap::printInfo() {
    for (int i = 0; i < partitionCount; i++) {
        cout << "Partition " << i + 1 << ": " << endl;
        cout << "\tSize: " << partitions[i].getSize() << " GB" << endl;
        cout << "\tFormat: " << partitions[i].getFormatString() << endl;
    }
    cout << endl;
}

void PartitionMap::printTechnicalInfo() {
    for (int i = 0; i < partitionCount; i++)
        cout << i + 1 << ": " << partitions[i].getSize() << " " << partitions[i].getFormatString() << endl;
    cout << endl;
}

void PartitionMap::deletePartition(int whatToDelete) {
    partitions[whatToDelete].setFormat(emptyspace);
    cout << "Partition " << whatToDelete + 1 << ", with " << partitions[whatToDelete].getFormatString() << " file system, was successfully deleted." << endl << endl;
    combineByDefault();
}

class Drive {
    private:
        double driveSize;
        string driveName;
    public:
        PartitionMap mainPartitionMap;
        void setInfo(double, string);
        void printInfo();
        double getDriveSize();
};

void Drive::setInfo(double desiredSize, string desiredName) {
    driveSize = desiredSize;
    driveName = desiredName;
    mainPartitionMap.setInitialPartition(emptyspace, driveSize);
}

void Drive::printInfo() {
    cout << "Size: " << driveSize << " GB" << endl;
    cout << "Name: " << driveName << endl;
}

double Drive::getDriveSize() {
    return driveSize;
}

class Run {
    public:
        char ask(bool);
        void run();
        void displayPartitionTable(Drive);
        void makeNewPartition(Drive);
        void deletePartition(Drive);
        void resizePartition(Drive);
        void formatPartition(Drive);
        //Drive setDriveToEdit();
};

char Run::ask(bool isThereADrive) {
    char tmp;

    if (isThereADrive) {
        cout << "(P)rint File System Info (Display Partition Table)" << endl;
        cout << "Make (N)ew Partition\t(D)elete Partition" << endl;
        cout << "(R)esize Partition\t(F)ormat Partition" << endl;
        cout << "(S)et Drive to Edit\t(Q)uit" << endl;
    }

    if (!isThereADrive) cout << "(A)dd New Drive\t(Q)uit Program" << endl;

    cout << "Action: ";
    cin >> tmp;
    cout << endl;

    return tmp;
}

void Run::run() {
    bool end = false;
    Drive drive;
    bool driveExists = false;

    while(!end) {
        char action = ask(driveExists);

        switch (action) {
            case 'p': case 'P':
                displayPartitionTable(drive);
                break;
            case 'n': case 'N':
                makeNewPartition(drive);
                break;
            case 'd': case 'D':
                deletePartition(drive);
                break;
            case 'r': case 'R':
                resizePartition(drive);
                break;
            case 'f': case 'F':
                formatPartition(drive);
                break;
            case 's': case 'S':
                //drive = setDriveToEdit();
                break;
            case 'a': case 'A': {
                    string name;
                    cout << "Drive Name: ";
                    cin >> name;
                    double size;
                    cout << "Drive Size: ";
                    cin >> size;
                    drive.setInfo(size, name);
                    drive.mainPartitionMap.insertInitIntoPartitionMap();
                    driveExists = true;
                    cout << endl;
                } break;
            case 'q': case 'Q':
                end = true;
                break;
        }
    }
}

void Run::displayPartitionTable(Drive currentDrive) {
    currentDrive.mainPartitionMap.printInfo();
}

void Run::makeNewPartition(Drive currentDrive) {

}

void Run::deletePartition(Drive currentDrive) {
    int partitionToDelete;
    currentDrive.mainPartitionMap.printTechnicalInfo();
    cout << "Which partition to delete? ";
    cin >> partitionToDelete;
    currentDrive.mainPartitionMap.deletePartition(partitionToDelete);
}

void Run::resizePartition(Drive currentDrive) {

}

void Run::formatPartition(Drive currentDrive) {

}

/*Drive Run::setDriveToEdit() {

}*/

#endif
```

Also, if you guys have any ideas to better it, let me know :)

---

### Post by nvteighen on 2008-06-01
A "segmentation fault" (aka "segfault") is when you try to access a variable outside its own limits. For example, this C code:

[PHP]
int main(void)
{
 int a[9]; /*a[0],...,a[8]*/

 int i;
 for(i = 0; i <= 9; i++)
 {
  a[i] = 0; 
 /*when i = 9, it will try to access a[9],
  *which is outside the array limits*/
 }

 return 0;
}
[/PHP]

I think you should understand it well if you know C++. (I don't know it...)

---

### Post by Zugzwang on 2008-06-01
Note that the error might also occur if you are accessing something that hasn't been allocated yet or you are accessing something that has already been deleted:
```

char *bla;
int m = bla[3]; // Using a "wild" pointer

```
and
```

char *bla = new char[10];
delete[] bla;
int m = bla[3]; // Usage after deletion

```

Now for fixing it, You might want to use the tool "valgrind" to check for memory leaks & illegal accesses. See the documentation for more information or run it from kdevelop, which will handle everything for you.  If you get a segmentation fault, then valgrind will spot where it occurred and why it occurred.

---

### Post by Martin Witte on 2008-06-01
g++ issues a backward warning when I compile your code, you can fix this by including <iostream>, the <iostream.h> you use is antique indeed. You don't give us a main where you instantiate these objects, maybe you can clarify what you we're doing when running these classes, and what actions lead to the fault

---

### Post by arseniy on 2008-06-01
main.cpp is:

```
#include <iostream>

using namespace std;

int main()
{
    Run control;
    control.run();
    cout << "Hello world!" << endl;
    return 0;
}
```

lol hello world :P there's kinda a practical purpose, just so i know that run() stopped correctly.

the main problem is the segmentation error
also, for some reason (if you read thru the code and everything) when i make 'control' print partition info, it doesn't print the format. any ideas why not?

---

### Post by Zugzwang on 2008-06-02
> **arseniy said:**
> 
the main problem is the segmentation error
also, for some reason (if you read thru the code and everything) when i make 'control' print partition info, it doesn't print the format. any ideas why not?

Read my post above to find out how to find the bug. If the segmentation fault occurs before the output buffer has been flushed, the output might be swallowed.

Also: If you post code here, *please* make sure it can be compiled directly. For example, your main.cpp won't compile since you didn't even include your header file.

By the way, it is not considered to be good style to include the implementations of non-inlined functions this way. But that has nothing to do with your bug.

---

### Post by skullmunky on 2008-06-03
More specifically, a segmentation fault is an attempt to access a memory location outside the memory segment for the program.  All processes get a chunk of memory, and aren't allowed to access memory outside of it.  Otherwise one process can thrash another process's stuff.  Bad.

90% of the time this happens to me because i used a pointer to an object before actually initializing it, so it just points to some random place.  it's also easy to get this by not bounds-checking an array.

In a quick look at your code I don't see where you initialize PartitionMap::partitions.  If that's true, then lines like

```

partitions[0].setFormat(initialPartition.getFormat());

```

will bomb because there IS no partitions[0].  there's no memory alloc'd for the array at all.

you can either allocate an array of some max number of possible partitions, or dynamically realloc the array as you make more, or make an array of pointers to partitions and use new to create them as needed.  or if you really want a dynamic array use a <vector>.

to elaborate on zugwang's suggestion, you usually put only the class and function definitions into the header file, e.g.:
```

class Partition {
    private:
        format partitionFormat;
        double partitionSize;
    public:
        void setFormat(format);
        void setSize(double);
        format getFormat();
        string getFormatString();
        double getSize();
};

```

and the all the actual implementations into source files (.cxx, .cpp, whatever you like for extensions), such as Partition.cxx, PartitionMap.cxx, main.cxx, and so on.  

I'm very sensitive to this style tip because nobody told me about it when -I- started in C, so I spent a whole year developing an architectural visualization walkthrough app for the 486 composed entirely of something like 20 or 30 header files.  

Also I don't know if you can return string objects like that.  You might want to make that function return a const string * instead.  

Also you will probably want to have constructors for your classes.

I don't know how much c++ experience you have yet so post back if none of that made any sense.  :p

---

