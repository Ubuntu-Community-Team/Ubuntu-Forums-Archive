---
title: "Care to suggest where I'm going wrong with this code?"
date: 2009-02-20
forum: Programming Talk
---

### Post by lswest on 2009-02-20
Okay, so I have a java program I'm working on, and I want to import the contents of a file into a custom linkedList.  The code worked fine until I added a loop which had the code running through every file in the directory and its subdirectories (which should just be added to the linkedList).  However, the code fails in a loop where it should actually go through fine, since it did so before.

code:
[PHP]public static RecordsLinkedList ReadInFromFile() throws IOException, FileNotFoundException{
		//initialize variables required for reading in
		String[] fResult={""};
		String projectName, projectID, date, description, client2;
		double rate, time;
		RecordsLinkedList returnValues=new RecordsLinkedList();
        
		//re-create the path to the file by making a File array of all files and subdirectories within the /Records folder
        String temp3=recurseInDirFrom(home+"/Records");
        String[] paths=temp3.split(",");
        File[] path=new File[paths.length];
        for(int z=0; z<paths.length;z++){
            path[z]=new File(paths[z].toString());
        }
		//run through the loop for all files contained within the /Records directory, if it's a directory do nothing
        for(int b=0; b<path.length; b++){
            if(!path[b].isDirectory()){
		//set up input tools
		FileReader fr=new FileReader(path[b]);
		BufferedReader input=new BufferedReader(fr);
		StringBuilder content=new StringBuilder();

		//initiate variables for result
		String line=null;
		String[] result;
		try{
		while((line=input.readLine())!=null){
			content.append(line);
			content.append(System.getProperty("line.seperator"));
		}
		}
		finally{
			input.close();
		}
		//split the contents of the file into sections
		result=content.toString().split("null");
		//set up the array and put each individual entry into a new position
		String[] result3=new String[result.length/4];
		int ind=0;
        System.out.println(result.length/4);
		for(int g=0; g<result.length+3;g+=4){
			if(ind!=(result.length/4)){
                System.out.println(ind+","+g);
				result3[ind]=result[g]+"\n"+result[g+1]+"\n"+result[g+2]+"\n"+result[g+3]; //error lies here, it only runs through this loop once!
				System.out.println("Result: "+result3[ind]);
				ind++;
			}
			else{
				continue;
			}
			//Remove duplicate entries from the array
			Set set = new HashSet(Arrays.asList(result3));
			fResult = (String[])(set.toArray(new String[set.size()]));
			for(int t=0; t<fResult.length; t++){
                System.out.println("--------------------------");
                System.out.println(fResult[t]);
                System.out.println("--------------------------");
				if(fResult[t]==null){
					fResult[t]="";
				}
			}
			for(int y=0; y<fResult.length; y++){
                System.out.println(fResult.length);
				String temp=fResult[y];
                System.out.println("--------------------------");
                System.out.println(temp);
                System.out.println("--------------------------");
				temp.replaceAll("null", "");
                System.out.println("--------------------------");
                System.out.println(temp);
                System.out.println("--------------------------");
				String[] tempArray=temp.split(":");
                System.out.println("--------------------------");
                System.out.println(tempArray.length);
                System.out.println("--------------------------");
				projectName=tempArray[1];
				projectID=tempArray[3];
				date=tempArray[5];
				description=tempArray[7];
				rate=Double.parseDouble(tempArray[9]);
				time=Double.parseDouble(tempArray[11]);
				client2=tempArray[13];
				Records temp2=new Records(projectName, projectID, rate, date, description, time, client2);
				returnValues.add(temp2);
			}
		}
        }
        }
		//return the final result LinkedList
		return returnValues;
	}[/PHP]

Example file:
> Project Name: John Childcare	ProjectID: JOHN311
Date: 8/12/08			Description: John's Childcare Services
Rate: 225.5			Time Spent: 6.0
Client: John Doe
Project Name: John Childcare	ProjectID: JOHN311
Date: 4/12/08			Description: John's Childcare Services
Rate: 220.5			Time Spent: 5.0
Client: John Doe
Project Name: John Childcare	ProjectID: JOHN311
Date: 8/12/08			Description: John's Childcare Services
Rate: 225.5			Time Spent: 6.0
Client: John Doe
Project Name: John Childcare	ProjectID: JOHN311
Date: 4/12/08			Description: John's Childcare Services
Rate: 220.5			Time Spent: 5.0
Client: John Doe
Project Name: John Childcare	ProjectID: JOHN311
Date: 8/12/08			Description: John's Childcare Services
Rate: 225.5			Time Spent: 6.0
Client: John Doe
Project Name: John Childcare	ProjectID: JOHN311
Date: 4/12/08			Description: John's Childcare Services
Rate: 220.5			Time Spent: 5.0
Client: John Doe

This is really frustrating, I can't help feeling I'm overlooking something simple :P  Any help would be greatly appreciated!

Thanks in advance,
Lswest

---

### Post by simeon87 on 2009-02-20
I would add some System.outs to see where it's going wrong.. is it really running through all files? Is it really going through the whole loop? Are the paths correctly determined?

I understand the frustration but you should narrow it down a bit because most of this code will be fine.

---

### Post by lswest on 2009-02-20
Sorry, I forgot to mention, I have already added S.O.P's, it creates the array of files correctly, however, it only runs through the loop once, then continues on until it encounters an array out of bounds exception (due to the fact that it's not taking in the entirety of the file).

Output from current S.O.P's:
> run:
12
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
0,0
Result: Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
--------------------------
null
--------------------------
--------------------------
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
--------------------------
2
--------------------------

        at projectdossier.Files.ReadInFromFile(Files.java:201)
        at projectdossier.Main.main(Main.java:25)
--------------------------
--------------------------

--------------------------
--------------------------
1
--------------------------
Java Result: 1
BUILD SUCCESSFUL (total time: 0 seconds)

Well, I S.O.P'd every relevant section again in this code:
[PHP]    public static RecordsLinkedList ReadInFromFile() throws IOException, FileNotFoundException{
		String[] fResult={""};
		String projectName, projectID, date, description, client2;
		double rate, time;
		RecordsLinkedList returnValues=new RecordsLinkedList();
        
		//re-create the path to the file
        String temp3=recurseInDirFrom(home+"/Records");
        String[] paths=temp3.split(",");
        File[] path=new File[paths.length];
        for(int z=0; z<paths.length;z++){
            path[z]=new File(paths[z].toString());
            System.out.print(path[z]);
        }
		//set up input tools
        for(int b=0; b<path.length; b++){
            System.out.println(b);
            if(!path[b].isDirectory()){
		FileReader fr=new FileReader(path[b]);
		BufferedReader input=new BufferedReader(fr);
		StringBuilder content=new StringBuilder();

		//initiate variables for result
		String line=null;
		String[] result;
		try{
		while((line=input.readLine())!=null){
			content.append(line);
			content.append(System.getProperty("line.seperator"));
            System.out.println(content.toString());
		}
		}
		finally{
			input.close();
		}
		//split the contents of the file into sections
		result=content.toString().split("null");
        for(int c=0; c<result.length; c++){
            System.out.println(result[c]);
        }
		//set up the array and put each individual entry into a new position
		String[] result3=new String[result.length/4];
        System.out.println(result3.length);
		int ind=0;
        System.out.println(result.length/4);
		for(int g=0; g<result.length+3;g+=4){
			if(ind!=(result.length/4)){
                System.out.println(ind+","+g);
				result3[ind]=result[g]+"\n"+result[g+1]+"\n"+result[g+2]+"\n"+result[g+3];
				System.out.println("Result: "+result3[ind]);
				ind++;
			}
			else{
				continue;
			}
			//Remove duplicate entries from the array
			Set set = new HashSet(Arrays.asList(result3));
			fResult = (String[])(set.toArray(new String[set.size()]));
			for(int t=0; t<fResult.length; t++){
                System.out.println("-----------Result run"+t+"---------------");
                System.out.println(fResult[t]);
                System.out.println("--------------------------");
				if(fResult[t]==null){
					fResult[t]="";
				}
			}
			for(int y=0; y<fResult.length; y++){
                System.out.println(fResult.length);
				String temp=fResult[y];
                System.out.println("-----------Result run"+y+"---------------");
                System.out.println(temp);
                System.out.println("--------------------------");
				temp.replaceAll("null", "");
                System.out.println("--------------------------");
                System.out.println(temp);
                System.out.println("--------------------------");
				String[] tempArray=temp.split(":");
                System.out.println("--------------------------");
                System.out.println(tempArray.length);
                System.out.println("--------------------------");
				projectName=tempArray[1];
				projectID=tempArray[3];
				date=tempArray[5];
				description=tempArray[7];
				rate=Double.parseDouble(tempArray[9]);
				time=Double.parseDouble(tempArray[11]);
				client2=tempArray[13];
				Records temp2=new Records(projectName, projectID, rate, date, description, time, client2);
				returnValues.add(temp2);
			}
		}
        }
        }
		//return the final result LinkedList
		return returnValues;
	}
[/PHP]

and the result of that was the following:
```
run:
/home/lswest/Records/home/lswest/Records/John Doe/home/lswest/Records/John Doe/JOHN311.txt/home/lswest/Records/Test Client/home/lswest/Records/Test Client/TEST314.txt0
1
2
Project Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
        at projectdossier.Files.ReadInFromFile(Files.java:208)
        at projectdossier.Main.main(Main.java:25)
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare Servicesnull
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0null
Project Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 8/12/08                        Description: John's Childcare ServicesnullRate: 225.5                        Time Spent: 6.0nullClient: John DoenullProject Name: John Childcare        ProjectID: JOHN311nullDate: 4/12/08                        Description: John's Childcare ServicesnullRate: 220.5                        Time Spent: 5.0nullClient: John Doenull
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
Project Name: John Childcare        ProjectID: JOHN311
Date: 4/12/08                        Description: John's Childcare Services
Rate: 220.5                        Time Spent: 5.0
Client: John Doe
12
12
0,0
Result: Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
-----------Result run0---------------
null
--------------------------
-----------Result run1---------------
Project Name: John Childcare        ProjectID: JOHN311
Date: 8/12/08                        Description: John's Childcare Services
Rate: 225.5                        Time Spent: 6.0
Client: John Doe
--------------------------
2
-----------Result run0---------------

--------------------------
--------------------------

--------------------------
--------------------------
1
--------------------------
Java Result: 1
BUILD SUCCESSFUL (total time: 0 seconds)

```

---

### Post by simeon87 on 2009-02-20
I'm unable to run the code which makes things tricky but could it be here?

```

if(ind!=(result.length/4)){
    // code
    ind++;
}
else{
    continue;
}

```

Let's say result.length = 12 and ind starts at 0. As long as ind is < 3, the code runs and ind is incremented. But as soon as ind is equal to result.length / 4, the code continues but ind is never incremented so it remains at its value and code in the if-statement never gets run anymore. In other words, it only runs once.

---

### Post by lswest on 2009-02-20
I thought about that too, but the current result.length's value is 48, so that result.length/4=12, and the ind integer never goes past the value "0".  Somehow it jumps out of the loop before increasing the value of ind.  That is, however, the area of the code that is creating the issue.  I just don't see why it jumps out of the loop before completing.

Also, if I comment out the "continue;" it still only runs once.

Lastly, if result.length is 12 I would only want the loop to run 3 times, since the file then only holds 3 entries.

---

### Post by lswest on 2009-02-22
Since I don't usually bump threads, but I could really use some help with this one, I will have to:

*bump*

*EDIT* Solved it, I had to close the for loop earlier (somehow the closing brace was at the end of the method).

---

