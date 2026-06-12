---
title: "Need help compiling a Half-Life hook"
date: 2011-10-02
forum: Packaging and Compiling Programs
---

### Post by w007 on 2011-10-02
Since this is my first post here, I'll introduce myself. I'm a gamer with a general love of all things computing, and I've been into it since my early years. Only just recently have I decided to try and get into programming. So far I'm not very good, and as a testament to this I can't get some code I found to compile. So to summarize, I thought you people could help me out.

It looks like my code/project (I'm using eclipse) is missing some crucial elements, but I don't know what they are. Code as follows:

```
#include <Windows.h>
#include <Tlhelp32.h>
#include <Shlwapi.h>
#include <Tchar.h>
#include <iostream>
#include <stdio.h>
 
using namespace std;

int main {
struct cvar
{
int active = 1
int vis_xqz = 6
}
int MyStudioDrawPlayer( int flags, entity_state_s *pplayer) = 1
{     
    int player;
    if(cvar.active && cvar.vis_xqz == 6)
    {
        glPolygonOffset(1.f,-20000.f);     //Change 2 parameter on different resolution (if needed)
        glEnable(GL_POLYGON_OFFSET_FILL); 
        player = StudioDrawPlayer( flags, pplayer );
        glDisable(GL_POLYGON_OFFSET_FILL);
    }
    else if(cvar.active && cvar.vis_xqz == 7)
    {
        int player_s;
        player = StudioDrawPlayer( flags, pplayer );
        if(player)
        {
            glDepthRange(0,0.5);
            player_s = StudioDrawPlayer( flags, pplayer );
            glDepthRange(0,1);
        }
    }
    else
    {
        player = StudioDrawPlayer( flags, pplayer );
    }

    return player;
}
void HLGuard_Bypass ()
{
    for( int ax = 1; ax < 33; ax++)
    {
        cl_entity_s *gMe = zEngfuncs->GetLocalPlayer();
        cl_entity_s *gpEnt = zEngfuncs->GetEntityByIndex( ax ); 
        pmtrace_t *cve;
        
        if( ( gpEnt != NULL ) && ( gpEnt->index != zEngfuncs->GetLocalPlayer()->index ) && ( gpEnt->curstate.solid ) && ( gpEnt->player ) && ( gpEnt->curstate.weaponmodel ) && ( !gpEnt->curstate.spectator ) && ( gpEnt->curstate.messagenum + 10 > zEngfuncs->GetLocalPlayer()->curstate.messagenum ) && zEngfuncs->GetLocalPlayer()->curstate.solid )
        { 

            cve = zEngfuncs->PM_TraceLine(gMe->origin, gpEnt->origin, 0, 2, -1); 

            if(cve->fraction < 1.0f)
            { 
                zEngfuncs->CL_CreateVisibleEntity(ET_NORMAL, gpEnt); 
            } 
        }
    }
}
}

```
Second project:
```
#include <Windows.h>
#include <Tlhelp32.h>
#include <Shlwapi.h>
#include <Tchar.h>
#include <iostream>
#include <stdio.h>
 
using namespace std;
char g_szInjectorPath[MAX_PATH] = "";
char szTarget[] = "hl.exe";
char szTarget_BIG[] = "HL.EXE";
//===========================================================================
DWORD dwGetGameProcessID(VOID)
{
    HANDLE hProcessSnapshot = CreateToolhelp32Snapshot(TH32CS_SNAPALL, NULL);

    PROCESSENTRY32 pe32;
    pe32.dwSize = sizeof(pe32);

    if(!Process32First(hProcessSnapshot, &pe32))
        return NULL;


        while(Process32Next(hProcessSnapshot, &pe32))
        {
            if(lstrcmp(pe32.szExeFile, szTarget) == 0 || (lstrcmp(pe32.szExeFile, szTarget_BIG) == 0))
            {
            return pe32.th32ProcessID;
            }
        }

    CloseHandle(hProcessSnapshot);

    return NULL;
}
//===========================================================================
char* szGetDirFile(char* szFileName)
{
    char szTemp[MAX_PATH] = "";

    if(wsprintf(szTemp, "%s%s", g_szInjectorPath, szFileName))
    {
        return szTemp;
    }

    return "";
}
//=============================================================================
BOOL bInjectLibrary(HANDLE hProcess, char* szDllToInjectPath)
{
    LPVOID lpRemoteAddress = VirtualAllocEx(hProcess, NULL, strlen(szDllToInjectPath), MEM_COMMIT, PAGE_READWRITE);

    if(!lpRemoteAddress)
        return FALSE;

    if(!WriteProcessMemory(hProcess, lpRemoteAddress, (LPVOID)szDllToInjectPath, strlen(szDllToInjectPath), NULL))
        return FALSE;

    HANDLE hThread = NULL;

    if(!(hThread = CreateRemoteThread(hProcess, NULL, NULL, (LPTHREAD_START_ROUTINE)GetProcAddress(GetModuleHandle("KERNEL32.DLL"), "LoadLibraryA"), lpRemoteAddress, NULL, NULL)))
        return FALSE;

    WaitForSingleObject(hThread, INFINITE);

    if(!VirtualFreeEx(hProcess, lpRemoteAddress, 0, MEM_RELEASE))
        return FALSE;

    CloseHandle(hThread);

    return TRUE;
}
//=============================================================================
int _tmain(int argc, _TCHAR* argv[])
{
    TOKEN_PRIVILEGES TPLEGES;

    TPLEGES.PrivilegeCount=1;
    TPLEGES.Privileges->Luid.LowPart=0x00000014;
    TPLEGES.Privileges->Luid.HighPart=0x00000000;
    TPLEGES.Privileges->Attributes=0x00000002;
    HANDLE htoken;
    OpenProcessToken(GetCurrentProcess(), TOKEN_ALL_ACCESS, &htoken);
    AdjustTokenPrivileges(htoken,0,&TPLEGES,0,0,0);
    
    GetModuleFileName(NULL, g_szInjectorPath, MAX_PATH);

    char* pos = g_szInjectorPath + strlen(g_szInjectorPath);
    while(pos >= g_szInjectorPath && *pos != '\\') --pos;
    pos[1] = 0;

    DWORD dwGamePID = dwGetGameProcessID();
    
        if(!dwGamePID)
        {
            Sleep(10);
            dwGamePID = dwGetGameProcessID();
        }

    HANDLE hProcess = OpenProcess(PROCESS_ALL_ACCESS, false, dwGamePID);

        if(!bInjectLibrary(hProcess, szGetDirFile("BLANK.dll")))
        {
        }

    CloseHandle(hProcess);

    return 1;
}
//==================================================

```

The error I'm getting is as follows:
make: *** No rule to make target `all'.


P.S. I use ubuntu, no need to convert me. hehe

---

