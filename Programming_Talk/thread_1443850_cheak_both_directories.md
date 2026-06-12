---
title: "cheak both directories"
date: 2010-03-31
forum: Programming Talk
---

### Post by ubash on 2010-03-31
Hi ALL,

Can u help me out in solving this problem in bash script
 
[LEFT][/LEFT]
[SIZE=3]Write a bash script with the following characteristics: [/SIZE]
[SIZE=3] 
[/SIZE][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script receives two paths, checks that they are both directories and prints errors if not. [/FONT]
[/SIZE][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script Take the list of files in dir1 and check if they exist in dir2. If the files have the same size in both directories, they are considered identical, else they are considered different. [/FONT]
[/SIZE][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script final output should be as follows (x, y, z are numbers): [/FONT]
[/SIZE][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]x *[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]files from [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1 *[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]are identical in [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path2*[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]: 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1/file_1 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1/file_2 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]…
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]Path1/file_x 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]y files from [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1 *[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]do not exist in [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path2*[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]: 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1/file_1 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1/file_2 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]…
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]Path1/file_y 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]z *[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]files are different in [/SIZE][/FONT][/SIZE][/FONT]*[FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path1 *[/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]and [/SIZE][/FONT][/SIZE][/FONT][I][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]path2 
[/I][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]file_1 xxx of dir1 has size ssss and date dddd time ttttt file_1 xxx of dir2 has size ssss and date dddd time ttttt”. 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]…
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]file_z xxx of dir1 has size ssss and date dddd time ttttt file_z xxx of dir2 has size ssss and date dddd time ttttt”. 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=2][FONT=Wingdings,Wingdings][SIZE=2]&#61607; [/SIZE][/FONT][/SIZE][/FONT][FONT=Courier New,Courier New][SIZE=2][FONT=Courier New,Courier New][SIZE=2]Total files in path1 are t. 
[/SIZE][/FONT][/SIZE][/FONT][B][FONT=Calibri,Calibri][SIZE=3][FONT=Calibri,Calibri][SIZE=3]Hints: 
[/B][/SIZE][/FONT][/SIZE][/FONT][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script can use ls -l with awk to extract the needed columns. [/FONT]
[/SIZE][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script can use grep, in addition to variables, loop and branch commands. [/FONT]
[/SIZE][FONT=Wingdings,Wingdings][SIZE=3][FONT=Wingdings,Wingdings][SIZE=3]&#61558; [/SIZE][/FONT][/SIZE][/FONT][SIZE=3][FONT=Times New Roman]The script can store intermediary data in temporary files in /tmp/ directory [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][/FONT][/SIZE] 
[SIZE=3][FONT=Times New Roman]plz :( help me [/FONT]
[/SIZE]

---

### Post by Elfy on 2010-03-31
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

Closed

---

