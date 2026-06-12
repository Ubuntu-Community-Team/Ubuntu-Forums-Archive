---
title: "Detect power failure"
date: 2010-11-13
forum: Programming Talk
---

### Post by WitchCraft on 2010-11-13
Question:

I have set the BIOS of my server to automagically restart the server after a power failure when power comes back.

Now I want to write a program that notifies me by email when the server has been rebooted after a powerfailure.

I didn't find a way to actually track a powerfailure event, but what I want to do is this:

Add a startup script and a shutdown script.

Then I have a SQlite db with these columns:
SESSION_UID, START_TIMESTAMP, STOP_TIMESTAMP

On startup, I write a new session uid + start time.
On shutdown, I get the uid of the last startup time, and update the data row with the shutdown time.

So on power failure, the last STOP_TIMESTAMP will be NULL when the startup script runs, which means I have successfully detected the power failure, and can send a message by email.

Now my question:
How to add a program at the right location into the startup/shudown scripts?
After all, on startup it must run after the network has been started, or else I can't send any email...
?

And the other question: Is this OK, or overly complicated, with anybody here having a better idea ?

---

### Post by WitchCraft on 2010-11-14
Below is what I have so far.
Now I still need to add it to the respective scripts. 

By hazard anybody knows the script location?

```


#ifdef __cplusplus
	#include <cstdio>
	#include <cstdlib>
	#include <ctime>
	//#include <cstdint>
	#include <cstdarg>
	#include <cstring>
	#include <cctype>
	
	#include <sqlite3.h>
#else
	#include <stdio.h>
	#include <stdlib.h>
	#include <time.h>
	//#include <stdint.h>
	#include <stdarg.h>
	#include <string.h>
	#include <ctype.h>

	#include <sqlite3.h>
#endif


#include <unistd.h> // for gethostname


// Requires:
// apt-get install sendemail


// Compile with:
// gcc -Wall -lsqlite3 powerfail.c -o hel
// g++ -Wall -lsqlite3 powerfail.c -o hel

// With stdint:
// g++ -Wall -Wno-write-strings -std=c++0x -lsqlite3 powerfail.c -o hel


// getconf GNU_LIBPTHREAD_VERSION
// getconf PAGESIZE

// Doc:
// http://stackoverflow.com/questions/1409453/how-to-store-and-get-datetime-value-in-sqlite
// http://docs.python.org/library/sqlite3.html
// http://www.devshed.com/c/a/Python/Using-SQLite-in-Python/


int bDebug = 0;
int bStartupRequested = 1;
int bShutdownRequested = 0;
int bSimulatePowerFailure = 0;
int bList = 0;
int bClear = 0;
int bTestMail = 0;


int Debug_Printf(const char* szFormat, ...)
{
	if(!bDebug)
		return 0;
	
	va_list arglist;
	int iReturnValue;
	
	int iSize = 100;
	char *p;
      
    if ((p = (char*) malloc (iSize)) == NULL)
    {
		printf("Error in Debug_Printf: Malloc failed.\n");
		return (int) NULL;
	}
	
	
	va_start(arglist, szFormat);
		iReturnValue = vsnprintf (p, iSize, szFormat, arglist);
    va_end(arglist);
    
    printf("%s", p);
    
    free(p);
    return iReturnValue;
}


char* ToLower(char* szInputString)
{
	if(szInputString != NULL)
	{
		int iStringLength = strlen(szInputString);
		char* szTempString = (char*) malloc((iStringLength+1) * sizeof(char));
		
		int i ;
		for(i =0; i < iStringLength; ++i)
			szTempString[i] = (char) tolower(szInputString[i]);
			
		return szTempString;
	}
	
	return NULL;
}


/* Callback called when the query is exceuted */
/*
static int callback(void *NotUsed, int argc, char **argv, char **azColName)
{
	printf ("\n ******** Inside Callback\n");
	int i;
	int rowpr=argc-1;
	NotUsed=0;
	printf("\n %s ",__FUNCTION__);
	
	for(i=0; i<rowpr; i++)
		printf("%s ",azColName[i]);

	printf("%s\n",azColName[rowpr]);



	for(i=0; i<rowpr; i++){
		printf("%s ",  argv[i] ? argv[i] : "NULL");

	}
	printf("%s\n",  argv[rowpr] ? argv[rowpr] : "NULL");

	return 0;
}
*/


void ExecuteNonQuery(char* szSQLstatement, sqlite3 *handle)
{
	Debug_Printf("SQL: %s\n", szSQLstatement);
	
	char* szErrMsg = NULL;
	// Execute the query
	int iExecutionResult = sqlite3_exec(handle, szSQLstatement, NULL, handle, &szErrMsg);
	if(iExecutionResult != SQLITE_OK)
	{
		if(szErrMsg != NULL)
		{
			Debug_Printf("\n\n******************************************************\n");
			Debug_Printf("* Error while doing ExecuteNonQuery: \n*\t%s\n", szErrMsg);
			Debug_Printf("******************************************************\n\n");
			sqlite3_free(szErrMsg);
		}

	}
}


void ClearTable(const char* szTableName, sqlite3 *handle)
{
	char* szDeleteStatement = (char*) malloc(1000 * sizeof(char));
	if(szDeleteStatement != NULL)
	{
		sprintf(szDeleteStatement, "DELETE FROM %s", szTableName);
		ExecuteNonQuery(szDeleteStatement, handle);
		free(szDeleteStatement);
	}
	else
		Debug_Printf("Error: Malloc failed. Insufficient RAM for DELETE statement allocation.\n");
}


int SelectFromTable(const char* szTableName, sqlite3 *handle)
{
	//char szSelectStatement[] = "SELECT * FROM T_StartStopLog ";
	char* szSelectStatement = (char*) malloc(1000 * sizeof(char));
	if(szSelectStatement != NULL)
	{
		sprintf(szSelectStatement, "SELECT * FROM %s", szTableName);
		
		sqlite3_stmt *stmt;
		// select query from the table
		int iRetVal = sqlite3_prepare_v2(handle, szSelectStatement, -1, &stmt, 0);
		if(iRetVal)
		{
			Debug_Printf("Selecting data from DB Failed\n");
			return -1;
		}
		
		// Read the number of rows fetched
		int cols = sqlite3_column_count(stmt);
		int col = 0;
		while(1)
		{
			// fetch a row's status
			iRetVal = sqlite3_step(stmt);
			
			if(iRetVal == SQLITE_ROW)
			{
				// SQLITE_ROW means fetched a row
				
				// sqlite3_column_text returns a const void* , typecast it to const char*
				for(col=0 ; col < cols; col++)
				{
					const char *val = (const char*)sqlite3_column_text(stmt,col);
					printf("%s = %s\t",sqlite3_column_name(stmt,col),val);
				}
				printf("\n");
			}
			else if(iRetVal == SQLITE_DONE)
			{
				// All rows finished
				Debug_Printf("All rows fetched\n");
				break;
			}
			else
			{
				// Some error encountered
				Debug_Printf("Some error encountered\n");
				return -1;
			}
		}
		
		
		free(szSelectStatement);
	}
	else
	{
		Debug_Printf("Error: Malloc failed. Insufficient RAM for SELECT statement allocation.\n");
		return -1;
	}
	
	return 0;
}


int GetScalarInt(const char* szSelectStatement, sqlite3 *handle)
{
	//char szSelectStatement[] = "SELECT * FROM T_StartStopLog ";
	
	int iReturnValue =0 ;
	
	if(szSelectStatement != NULL)
	{
		sqlite3_stmt *stmt;
		// select query from the table
		int iRetVal = sqlite3_prepare_v2(handle, szSelectStatement, -1, &stmt, 0);
		if(iRetVal)
		{
			Debug_Printf("Selecting data from DB Failed\n");
			return -1;
		}
		
		// Read the number of rows fetched
		int cols = sqlite3_column_count(stmt);
		int col = 0;
		
		
		
		while(1)
		{
			// fetch a row's status
			iRetVal = sqlite3_step(stmt);
			
			if(iRetVal == SQLITE_ROW)
			{
				// SQLITE_ROW means fetched a row
				
				// sqlite3_column_text returns a const void* , typecast it to const char*
				for(col=0 ; col < cols; col++)
				{
					const char *val = (const char*)sqlite3_column_text(stmt,col);
					Debug_Printf("%s = %s\n",sqlite3_column_name(stmt,col),val);
					
					if(val != NULL)
					{
						iReturnValue= atoi(val);
					}
					else
						iReturnValue = 0;
				}
				Debug_Printf("\n");
			}
			else if(iRetVal == SQLITE_DONE)
			{
				// All rows finished
				Debug_Printf("All rows fetched\n");
				break;
			}
			else
			{
				// Some error encountered
				Debug_Printf("Some error encountered\n");
				return -1;
			}
		}
		
		
		//free(szSelectStatement);
	}
	else
	{
		Debug_Printf("Error: No valid query-parameter passed to function GetScalarInt.\n");
		return -1;
	}
	
	return iReturnValue;
}




// http://www.cplusplus.com/reference/clibrary/ctime/tm/	
int GetSequentialDate(int iDay, int iMonth, int iYear, int iHour, int iMinute, int iSecond)
{
	struct tm a_tm_struct ;
	a_tm_struct.tm_year = iYear - 1900;
	a_tm_struct.tm_mon = iMonth - 1;
	a_tm_struct.tm_mday = iDay;
	a_tm_struct.tm_hour = iHour;
	a_tm_struct.tm_min = iMinute;
	a_tm_struct.tm_sec = iSecond;
	
	
	//time_t mktime( struct tm * ptm );
	//time_t xy = mktime(&a_tm_struct);
	return  (int) mktime(&a_tm_struct);
}


int Now()
{
	/*
	time_t now = time(NULL);
	char szTime[100] ;
	sprintf(szTime, "%d", (int) now);
	printf("Time: %s\n", szTime);
	*/
	
	return (int) time(NULL);
}


// http://www.gamedev.net/community/forums/topic.asp?topic_id=399702
char* GetLocalTime(int iSequentialDate)
{
	time_t tThisTime = (time_t) iSequentialDate;
	
	struct tm  *ts;
	ts = localtime(&tThisTime);
	//ts = gmtime ( &tThisTime );
	
	char* szBuffer = (char*) malloc(80 * sizeof(char));
	//strftime(buf, sizeof(buf), "%a %Y-%m-%d %H:%M:%S %Z", ts);
	strftime(szBuffer, 80, "%A %d.%m.%Y %H:%M:%S %Z", ts);
	
	Debug_Printf("%s\n", szBuffer);
	return szBuffer;
}


// apt-get install mailutils
// apt-get install sendemail
void SendMail()
{
	char szHostname[128];
	gethostname(szHostname, sizeof szHostname);
	Debug_Printf("Current hostname: %s\n", szHostname);
	
     // /usr/bin/mail ~'TEST' -s 'MailMngr Message' -t 'somebody@example.com'	
	//sendemail -f powerfail.hostname@localhost -t somebody@exymple.com -u "subj" -m "hello" -s "smtp.example.com"
	char* szMailCommand = (char*) malloc(1000* sizeof(char));
	char szSender[250] ;
	sprintf(szSender, "powerfail.%s@localhost", szHostname);
	char szReceiver[] = "reciever@example.com";
	char szSubject[] = "Power-failure";
	
	char* szCurrentTime = GetLocalTime(Now());
	char* szMessage = (char*) malloc(1000);
	sprintf(szMessage, "Your humble server has suffered a fatal powerfailure and recovered now (%s).", szCurrentTime);
	char szServer[] = "smtp.example.com";
	
	
	sprintf(szMailCommand, "sendemail -f %s -t %s -u \"%s\" -m \"%s\" -s \"%s\"", szSender, szReceiver, szSubject, szMessage, szServer);
	free(szCurrentTime);
	free(szMessage);
	Debug_Printf("szMailCommand: %s\n", szMailCommand); 
	
	FILE* mFile = popen(szMailCommand, "w");
	pclose(mFile);
	
	free(szMailCommand);
}


int OnStartup()
{
	Debug_Printf("Entering OnStartup.\n");
	
    sqlite3 *handle;
    int iSQLconnectionError = sqlite3_open("PowerlossDetectionDB.sqlite3", &handle);
	if(iSQLconnectionError)
	{
		// If connection failed, handle returns NULL
		Debug_Printf("Database connection failed\n");
		return -1;
	}
	Debug_Printf("Connection successful\n");
	
	
	char szCreateTableStatement[] = "CREATE TABLE IF NOT EXISTS T_StartStopLog (SSL_Session_UID INTEGER PRIMARY KEY, SSL_StartTime INTEGER NOT NULL, SSL_StopTime INTEGER)";	
	ExecuteNonQuery(szCreateTableStatement, handle);
	
	
    
    int iLastStartupEntry = GetScalarInt("SELECT MAX(SSL_StartTime) FROM T_StartStopLog", handle);
    if(iLastStartupEntry!= 0)
    {
		char* szLastStartupTime = GetLocalTime(iLastStartupEntry);
		printf("Last startup-date:\t%s\n", szLastStartupTime);
		free(szLastStartupTime);
    }
    else
		printf("This is the first-time startup with PowerFailure tracking!\n");
    
    char* szQuery = (char*) malloc(1000* sizeof(char));
		sprintf(szQuery, "SELECT SSL_Session_UID FROM T_StartStopLog WHERE SSL_StartTime = %d", iLastStartupEntry);
		int iLastSession = GetScalarInt(szQuery, handle);
		Debug_Printf("Last session: %d\n", iLastSession);
		
		sprintf(szQuery, "SELECT SSL_StopTime FROM T_StartStopLog WHERE SSL_Session_UID = %d", iLastSession);
		int iLastShutdownEntry = GetScalarInt(szQuery, handle);
    free(szQuery);
    
    if(iLastSession != 0)
    {
		if(iLastShutdownEntry == 0)
		{
			Debug_Printf("Sending powerfail notification.\n");
			SendMail();
			Debug_Printf("Powerfail notification sent.\n");
		}
		else
		{
			char* szLastShutdownTime = GetLocalTime(iLastShutdownEntry);
			printf("Last shutdown-date:\t%s\n", szLastShutdownTime);
			free(szLastShutdownTime);
		}
    }
    
    
    char szInsertStatement[1000];
	int iUID = ++iLastSession;
	Debug_Printf("iUID: %d\n", iUID);
	
	if(iUID != 0)
	{
			sprintf(szInsertStatement, "INSERT INTO T_StartStopLog VALUES(%d, %d, NULL)", iUID, Now());
			ExecuteNonQuery(szInsertStatement, handle);
	}
	else
		Debug_Printf("Error, last UID could not be determined...");
	
    if(!iSQLconnectionError)
		sqlite3_close(handle);
	else
		Debug_Printf("Not closing connection.\n");
    
    Debug_Printf("Exiting OnStartup.\n");
	return EXIT_SUCCESS;	
}


int OnShutDown(int bSimulatePowerFail)
{
	Debug_Printf("Entering OnShutDown.\n");
	
	sqlite3 *handle;
    int iSQLconnectionError = sqlite3_open("PowerlossDetectionDB.sqlite3",&handle);
	if(iSQLconnectionError)
	{
		// If connection failed, handle returns NULL
		Debug_Printf("Database connection failed\n");
		return -1;
	}
	Debug_Printf("Connection successful\n");
	
    char szInsertStatement[1000];
	int iUID = GetScalarInt("SELECT MAX(SSL_Session_UID) FROM T_StartStopLog", handle);
	
	if(iUID == -1)
	{
		Debug_Printf("Error, last UID could not be determined...");
		
		if(!iSQLconnectionError)
			sqlite3_close(handle);
		
		return EXIT_FAILURE;
	}
	
	if(!bSimulatePowerFail)
	{
		sprintf(szInsertStatement, "UPDATE T_StartStopLog SET SSL_StopTime = %d WHERE SSL_Session_UID = %d", Now(), iUID);
		ExecuteNonQuery(szInsertStatement, handle);	
    }
    else
		Debug_Printf("Simulated power failure !\n");
    
    
    if(!iSQLconnectionError)
		sqlite3_close(handle);
	else
		Debug_Printf("Not closing connection.\n");
    
    
	Debug_Printf("Exiting OnShutDown.\n");
	return EXIT_SUCCESS;
}


int Clear()
{
	Debug_Printf("Entering Clear.\n");
	
	sqlite3 *handle;
    int iSQLconnectionError = sqlite3_open("PowerlossDetectionDB.sqlite3",&handle);
	if(iSQLconnectionError)
	{
		// If connection failed, handle returns NULL
		Debug_Printf("Database connection failed\n");
		return EXIT_FAILURE;
	}
	Debug_Printf("Connection successful\n");
	
	ClearTable("T_StartStopLog", handle);
	
	if(!iSQLconnectionError)
		sqlite3_close(handle);
	else
		Debug_Printf("Not closing connection.\n");
    
	Debug_Printf("Exiting Clear.\n");
	return EXIT_SUCCESS;
}


int List()
{
	Debug_Printf("Entering List.\n");
	
	sqlite3 *handle;
    int iSQLconnectionError = sqlite3_open("PowerlossDetectionDB.sqlite3",&handle);
	if(iSQLconnectionError)
	{
		// If connection failed, handle returns NULL
		Debug_Printf("Database connection failed\n");
		return EXIT_FAILURE;
	}
	Debug_Printf("Connection successful\n");
	
	SelectFromTable("T_StartStopLog", handle);
	
	if(!iSQLconnectionError)
		sqlite3_close(handle);
	else
		Debug_Printf("Not closing connection.\n");
    
    
	Debug_Printf("Exiting List.\n");
	return EXIT_SUCCESS;
}


int SwitchArgs(int argc, char* argv[])
{
	int i;
	for(i=0; i < argc; ++i)
	{
		if(i==0)
			continue;
		
		Debug_Printf("argv[%d] = %s\n", i, argv[i]);
		char* szThisArgument = ToLower(argv[i]);
		Debug_Printf("szThisArgument: %s\n", szThisArgument);
		
		if(!strcmp(szThisArgument, "--debug"))
		{
			Debug_Printf("Debug requested...\n");
			bDebug = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "-dg"))
		{
			Debug_Printf("Debug requested...\n");
			bDebug = 1;
			free(szThisArgument);
			continue;
		}
		
		if(!strcmp(szThisArgument, "-shutdown"))
		{
			Debug_Printf("Shutdown requested...\n");
			bShutdownRequested = 1;
			bStartupRequested = 0;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "-d"))
		{
			Debug_Printf("Shutdown requested...\n");
			bShutdownRequested = 1;
			bStartupRequested = 0;
			free(szThisArgument);
			continue;
		}
		
		
		if(!strcmp(szThisArgument, "-s"))
		{
			Debug_Printf("Startup requested...\n");
			bStartupRequested = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "--startup"))
		{
			Debug_Printf("Startup requested...\n");
			bStartupRequested = 1;
			free(szThisArgument);
			continue;
		}
		
		if(!strcmp(szThisArgument, "-s"))
		{
			Debug_Printf("Powerfail-simulation requested...\n");
			bSimulatePowerFailure = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "--simulate"))
		{
			Debug_Printf("Powerfail-simulation requested...\n");
			bSimulatePowerFailure = 1;
			free(szThisArgument);
			continue;
		}
		
		if(!strcmp(szThisArgument, "-l"))
		{
			Debug_Printf("List requested...\n");
			bList = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "--list"))
		{
			Debug_Printf("List requested...\n");
			bList = 1;
			free(szThisArgument);
			continue;
		}
		
		if(!strcmp(szThisArgument, "-c"))
		{
			Debug_Printf("Clear requested...\n");
			bClear = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "--clear"))
		{
			Debug_Printf("Clear requested...\n");
			bClear = 1;
			free(szThisArgument);
			continue;
		}
		
		
		if(!strcmp(szThisArgument, "-t"))
		{
			Debug_Printf("Testmail requested...\n");
			bTestMail = 1;
			free(szThisArgument);
			continue;
		}
		else if(!strcmp(szThisArgument, "--testmail"))
		{
			Debug_Printf("Testmail requested...\n");
			bTestMail = 1;
			free(szThisArgument);
			continue;
		}
		
		printf("Usage error: Argument %s is not a valid argument.\nTerminating program.\n\n", szThisArgument);
		free(szThisArgument);
		return EXIT_FAILURE;
	}
	
	return EXIT_SUCCESS;	
}




int main(int argc, char* argv[])
{
	SwitchArgs(argc, argv);
	
	/*
	int iSeqDate = GetSequentialDate(31, 12, 2010, 23, 59, 59);
	char* szDate = GetLocalTime(iSeqDate);
	printf("Sequential date: %s\n", szDate);
	
	time_t result = time(NULL);
	printf("%s%ju secs since the Epoch\n", asctime(localtime(&result)), (uintmax_t) result);
	*/
	
	if(bTestMail)
	{
		SendMail();
		return EXIT_SUCCESS;
	}
	
	    
    if(bClear)
	{
		Debug_Printf("Calling Clear\n");
		Clear();
	}
    
    
    if(bStartupRequested)
    {
		Debug_Printf("Calling OnStartup\n");
		OnStartup();
    }
    
    
    if(bShutdownRequested)
	{
		Debug_Printf("Calling OnShutDown\n");
		OnShutDown(bSimulatePowerFailure);
	}
	
	
	if(bList)
	{
		Debug_Printf("Calling List\n");
		List();
	}
	
	
	Debug_Printf("Powerfail notification finished !\n");
	return EXIT_SUCCESS;
}

```

---

### Post by WitchCraft on 2010-11-15
bump.

Script locations for entering a reference to this program on startup and shutdown.
On startup when the network has been started (ideally also WLAN).

---

### Post by WitchCraft on 2010-11-15
I've cross-posted this question to
[http://stackoverflow.com/questions/4187183/linux-where-to-put-a-startup-and-shutdown-task](http://stackoverflow.com/questions/4187183/linux-where-to-put-a-startup-and-shutdown-task)

---

### Post by radeon21 on 2010-11-15
I think the simplest solution would be to add an entry in the Startup Applications (System > Preferences > Startup Applications) that sends an email during any reboot.  Presumably you know when the normal reboots are occurring and you could just ignore those emails.

If you want to go the more complicated route, I think that the legit way to run your script at startup and shutdown is to put it in /etc/init.d and then make symlinks to /etc/rc0.d and /etc/rc6.d.  There's also a tool update-rc.d that is used in installing init scripts into the correct rc#.d directories (I don't remember if it is 100% necessary).  It's been quite a while since I've messed with that stuff so you'll have to work out the details yourself, but that should get you started.

---

### Post by WitchCraft on 2010-11-16
Ah rc.0 for shutdown rc.5 for init.

This is the info I needed:
[http://www.linux.com/archive/feature/114107](http://www.linux.com/archive/feature/114107)
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

PS: Somebody else has come up with a far simpler solution:

```

#!/bin/bash

SHUTDOWNFILE=/etc/normalshutdown

if [ ${1} = "stop" ] then touch "${SHUTDOWNFILE}"
elif [ ${1} = "start" ] 
then 
    if [ ! -e "${SHUTDOWNFILE}" ] 
    then 
        mail -s "Power failure, recovered" admin@host.net
    else
        rm "${SHUTDOWNFILE}"
    fi
fi

```

---

