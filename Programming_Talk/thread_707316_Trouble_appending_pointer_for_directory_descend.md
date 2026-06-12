---
title: "Trouble appending pointer for directory descend"
date: 2008-02-25
forum: Programming Talk
---

### Post by NuNn DaDdY on 2008-02-25
I'm trying to make a program in which I go through the file hierarchy and print out the name without using recursion.  However, when I try to just append my pointer for future descending I am unable to do so and instead just overwrite the pointer.  Here is the copy of the troublesome code:


int main(int argc, char *argv[]) {
        DIR *dp;
        struct stat statbuf;
        struct dirent *dirp;

        static char *fullpath;
        char *dirQueue[512];
        char *ptr;

        if(argc != 2)
                err_quit("Error: Invalid Input, Please Use <a.out> <target directory>\n");

        fullpath = argv[1];


        if(lstat(fullpath, &statbuf) < 0)
                err_sys("Error: Stat Error for %s\n", fullpath);


        if(S_ISDIR(statbuf.st_mode) == 0)       //Not a directory
                err_sys("Error: Please provide a directory to display.\n");


        ptr = fullpath + strlen(fullpath); //Point to end of fullpath
        *ptr++ = '/';
        *ptr = 0;


        if((dp = opendir(fullpath)) == NULL)
                err_sys("Error:  Cannot read %s", fullpath);


        while((dirp = readdir(dp)) != NULL) {
                if(strcmp)dirp->d_name, ".") == 0 || strcmp(dirp->d_name, "..") == 0)      //Ignore dot and dot-dot
                              continue;

                strcpy(ptr, dirp->d_name);

                printf("%s\n", ptr);

                *ptr++ = '/';
                *ptr = 0;
        }

        exit(0);
}


NOTE:   I know that the code is incomplete but all I need to accomplish at the moment is this small issue, thanks everyone.

---

### Post by Zugzwang on 2008-02-25
You will need to "emulate" a stack of the variables of each level needed at each level of descending to do this without recursion. May I ask what is the reason you don't want to use it?

---

