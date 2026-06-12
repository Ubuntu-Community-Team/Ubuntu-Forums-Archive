---
title: "parsing arguments in a server-client model application"
date: 2006-12-16
forum: Programming Talk
---

### Post by NitrOuS on 2006-12-16
Hi!I try to develop a program with internet sockets in server-client model to make a dns server. The client is a telnet window. The only thing that I have to worry about is to develop the server to server the clients' requests. But I'm having a problem in parsing the arguments from the telnet terminal...I want to find a way to make the arguments discrete. I found a way but it doesn't seem to work. Although the arguments seem to pass from client to server right and the 2nd argument is the right one when I use it to gethostbyname() function the result is always the same... [COLOR="Red"]Unknown host[/COLOR]. Did anyone face sometime this kind of problem?Do you have any idea of what is happening?Any help is welcome...Thanx in advance

Here is the code for parsing the second argument.Argument line is the whole line read, buffer is a storage array and length_nm is the length of the first argument.
[FONT="Lucida Console"]int parse_second(char line[],char buffer[],int length_nm){
    int length_line;
    int counter,counter1;
    char *str_sth;
    counter=length_nm;
    counter1=0;
    length_line=strlen(line);
    if(length_nm<(length_line-2)){//checking if there are the right number of arguments.If yes continue
       
        while((line[counter]!='\n')&&(line[counter]!='\n')){
            buffer[counter1]=line[counter];
            counter++;
            counter1++;
        }
        str_sth=strtok(buffer," ");//ignore another argument if present... 
    }
    else{//else return -1
        return -1;
    }
    return 0;
}
[/FONT]

---

