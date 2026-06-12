---
title: "Vari_Cyph_FB_V_14"
date: 2019-02-07
forum: Programming Talk
---

### Post by albert-redditt on 2019-02-07
Worlds Strongest Cypher Program... Vari_Cyph_FB_V_14


'VariCyph FreeBasic Version 12.0
'FreeBASIC available at FreeBasic.net
'popular IDE's
'FBIDE , FBIDE.net
'Geany IDE
'
'Written by Albert Redditt
'
'albert_redditt@yahoo.com

#define WIN_INCLUDEALL
#Include once "windows.bi"
#Include once "/win/commctrl.bi"
#Include once "file.bi"

'===============================================================================
'===============================================================================
Private function fb_Set_Font (Font As String,Size As Integer,Bold As Integer,Italic As Integer,Underline As Integer,StrikeThru As Integer) As HFONT
  Dim As HDC hDC=GetDC(HWND_DESKTOP)
  Dim As Integer CyPixels=GetDeviceCaps(hDC,LOGPIXELSY)
  ReleaseDC(HWND_DESKTOP,hDC)
  Return CreateFont(0-(Size*CyPixels)/72,0,0,0,0,0,0,0, OEM_CHARSET  _
  ,OUT_TT_PRECIS,CLIP_DEFAULT_PRECIS,DEFAULT_QUALITY,FF_DONTCARE,Font)
End Function

Dim As HFONT   fonthdl
Dim As String  fontname
Dim As Integer fontsize = 12
fontname = "Terminal"
fonthdl = fb_Set_Font(fontname, fontsize,0,0,0,0)


'===============================================================================
'===============================================================================
Dim Shared As Long trackpos1 , getlast1=1
Dim Shared As Long trackpos2 , getlast2=1
'===============================================================================
'===============================================================================
Dim shared as integer TabPages    : TabPages     = 1
Dim Shared as integer GarbageBits : GarbageBits  = 64
Dim Shared as integer GarbageBytes: GarbageBytes = 1
'===============================================================================
'===============================================================================
const Keys_Spinner_Val_max = 1024
const Keys_Spinner_val_min = 8
const Keys_Spinner_val_inc = 8
dim shared as uinteger Keys_Spinner_val = 8
 
const Garbage_Spinner_Val_max = 128
const Garbage_Spinner_val_min = 1
const Garbage_Spinner_val_inc = 1
dim shared as uinteger Garbage_Spinner_val = 1
'===============================================================================
'===============================================================================

dim shared as string file , extension , FileData

Redim shared as integer Key(0 to (64*TabPages)-1)
Redim shared as Ubyte SubKey(0 to 15)

for a as longint = lbound(key) to ubound(key)
    key(a) = a
next

Declare sub PrintKey()

Declare sub LoadCypheredText()
Declare sub Cypher()
Declare sub DeCypher()

Declare sub GetKeys()
Declare sub LoadKey()
Declare sub SaveKey()
Declare sub SaveOutput()

Declare sub GenerateKey()
Declare sub GenerateSubKey()
Declare sub CopyOutputToInput()

Declare sub MessageSpinner_Up()
Declare sub MessageSpinner_Dn()
Declare sub MessageSize()
Declare sub GarbageSpinner_Up()
Declare sub GarbageSpinner_Dn()
Declare sub GarbageSize()

Declare sub GetFileName()

ReDim shared as hwnd STATICS(1 to TabPages)
ReDim shared as hwnd EDIT_KEY(1 to TabPages,1 to 8,1 to 8)

Dim shared as string Help_Text
    Help_Text = "This encoder is a bit scrambler." + chr(13) + chr(10)
    Help_Text+= "It can only load ASCII text files 8 bit." + chr(13) + chr(10)
    Help_Text+= chr(13)+chr(10)
    Help_Text+= "It scrambles message bytes amongst several times as many garbage bytes." + chr(13) + chr(10)
    Help_Text+= "You select the number of message bytes. in multiples of 8" + chr(13) + chr(10)
    Help_Text+= "Then" + chr(13) + chr(10)
    Help_Text+= "You select the number of garbage bytes as a multiple of message bytes 1x , 2x , 4x etc.." + chr(13) + chr(10)
    Help_Text+= "If garbage is set to 4 then the output will be 4 times as long as the message bytes." + chr(13)+chr(10)
    Help_Text+= chr(13)+chr(10)
    Help_Text+= "If message bytes is set to 16 then the message is broken into chunks of 16 bytes." + chr(13) + chr(10)
    Help_Text+= "Message blocks can be any multiple of 8 , up to 1024."+chr(13)+chr(10)
    Help_Text+= "Garbage blocks can be any multiple of MessageBlocks up to 128."+chr(13)+chr(10)
    Help_Text+= chr(13)+chr(10)
    Help_Text+= chr(13)+chr(10)
    Help_Text+= "If the cyphered message doesn't show up in the bottom window"+chr(13)+chr(10)
    Help_Text+= "click on the window and play with the scroll bar to get the message to show up."+chr(13)+chr(10)
    Help_Text+= chr(13)+chr(10)
    Help_Text+= "Written in FreeBasic for Windows , by [email]albert_redditt@yahoo.com[/email]"
       
Dim shared As MSG msg     ' Message variable (stores massages)
Dim shared As HWND hWnd _
                   , EDIT_IN _
                   , EDITKEY _
                   , STATIC_OUTS(0 to 15) _
                   , EDIT_OUTS(0 to 15) _
                   , EDIT_OUT _
                   , LOADCYPHTEXT_BTN _
                   , CYPHER_BTN _
                   , DECYPHER_BTN _
                   , LOADKEY_BTN _
                   , SAVEKEY_BTN _
                   , GENERATEKEY_BTN _
                   , label1 _
                   , MESSAGE_SIZE _
                   , label2 _
                   , GARBAGE_SIZE _
                   , HELP _
                   , GENERATESUBKEY_BTN _
                   , SAVEOUTPUT_BTN _
                   , COPY_OUTPUT_TO_INPUT _  'for multiple cyphering.
                   , TrackBar1 _
                   ,TrackBar2
'===============================================================================                   
' Create window
hWnd = CreateWindowEx( 0, "#32770", "Vari_Cyph_FB_V12  Feb / 2017", WS_OVERLAPPEDWINDOW Or WS_VISIBLE, 100, 100, 600, 600, 0, 0, 0, 0 )

'create in edit
EDIT_IN  = CreateWindowEx( 0, "EDIT", "", WS_VISIBLE Or WS_CHILD Or WS_BORDER or ES_MULTILINE or WS_VSCROLL or WS_HSCROLL  , 10, 10,430,110, hWnd, 0, 0, 0 )
SendMessage(EDIT_IN,WM_SETFONT,Cast(WPARAM,fonthdl),0)

'create readonly edit out
EDIT_OUT = CreateWindowEx( 0, "EDIT", "", WS_VISIBLE Or WS_CHILD Or WS_BORDER or ES_MULTILINE or WS_VSCROLL or WS_HSCROLL , 10,430,430,130, hWnd, 0, 0, 0 )
SendMessage(EDIT_OUT,WM_SETFONT,Cast(WPARAM,fonthdl),0)

'create key edit
EDITKEY = CreateWindowEx( 0, "EDIT", "", WS_VISIBLE Or WS_CHILD Or WS_BORDER or ES_MULTILINE or WS_VSCROLL or WS_HSCROLL or ES_readonly, 10,125,430,215, hWnd, 0, 0, 0 )

'create labels and edits for output.
dim as integer count1
for y as integer = 1 to 2 step 1
    for x as integer = 1 to 8 step 1
       count1 = ((y*8)-8)+x-1
       SubKey(count1)=(65+count1)
       STATIC_OUTS(count1) = CreateWindowEx( 0,"STATIC", right("0000" + bin(count1),4), WS_VISIBLE Or WS_CHILD             ,(x*38)-38+(15*x) ,280+( (y*12)+20+(32*y)) , 38, 20, hWnd, 0, 0, 0 )
       EDIT_OUTS( count1 ) = CreateWindowEx( 0,"EDIT"  , CHR(SubKey(count1))          , WS_VISIBLE Or WS_CHILD Or WS_BORDER,(x*38)-30+(15*x) ,305+( (y*12)+10+(32*y)) , 18, 20, hWnd, 0, 0, 0 )
   next
next

LOADCYPHTEXT_BTN  = CreateWindowEx( 0,"BUTTON"  , "Load Cypher"  , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,10 , 100, 25, hWnd, 0, 0, 0 )
CYPHER_BTN        = CreateWindowEx( 0,"BUTTON"  , "Cypher"       , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,50 , 100, 25, hWnd, 0, 0, 0 )
DECYPHER_BTN      = CreateWindowEx( 0,"BUTTON"  , "DeCypher"     , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,90 , 100, 25, hWnd, 0, 0, 0 )

LOADKEY_BTN       = CreateWindowEx( 0,"BUTTON"  , "Load Key"     , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,130 , 100, 25, hWnd, 0, 0, 0 )
SAVEKEY_BTN       = CreateWindowEx( 0,"BUTTON"  , "Save Key"     , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,160 , 100, 25, hWnd, 0, 0, 0 )
GENERATEKEY_BTN   = CreateWindowEx( 0,"BUTTON"  , "Generate Key" , WS_VISIBLE Or WS_CHILD Or WS_BORDER,460 ,190 , 100, 25, hWnd, 0, 0, 0 )

label1                        = CreateWindowEx( 0,"STATIC"    , "Message Size"      ,  WS_VISIBLE or WS_CHILD or WS_BORDER  ,460 ,225 , 100, 20, hWnd, 0, 0, 0 )   
MESSAGE_SIZE    = CreateWindowEx( 0,"STATIC"    , str(TabPages*8)     , WS_VISIBLE Or WS_CHILD Or WS_BORDER  ,460 ,245 , 100, 25, hWnd, 0, 0, 0 )
TrackBar1  = CreateWindowEx(NULL,TRACKBAR_CLASS, "Trackbar Control", WS_VISIBLE Or WS_CHILD Or  TBS_AUTOTICKS Or TBS_ENABLESELRANGE, 450, 270,120, 35, hwnd,0,0,0)
SendMessage(TrackBar1, TBM_SETRANGE,TRUE, MAKELONG(1,1024\8))'TRACKBAR 1 to 128

label2               = CreateWindowEx( 0,"STATIC"    , "Garbage Size"      , WS_VISIBLE or WS_CHILD or WS_BORDER  ,460 ,310 , 100, 20, hWnd, 0, 0, 0 )   
GARBAGE_SIZE  = CreateWindowEx( 0,"STATIC"    , str(GarbageBytes)   , WS_VISIBLE Or WS_CHILD Or WS_BORDER   ,460 ,330 ,  100, 25, hWnd, 0, 0, 0 )
TrackBar2  = CreateWindowEx(NULL,TRACKBAR_CLASS, "Trackbar Control", WS_VISIBLE Or WS_CHILD Or  TBS_AUTOTICKS Or TBS_ENABLESELRANGE, 450, 355,120, 35, hwnd,0,0,0)
SendMessage(TrackBar2, TBM_SETRANGE,TRUE, MAKELONG(1,128))'TRACKBAR 1 to 128

GENERATESUBKEY_BTN= CreateWindowEx( 0,"BUTTON" ,"Generate SubKey", WS_VISIBLE Or WS_CHILD Or WS_BORDER,445 ,395 , 130, 25, hWnd, 0, 0, 0 )

SAVEOUTPUT_BTN    = CreateWindowEx( 0,"BUTTON" ,  "Save Output"  , WS_VISIBLE Or WS_CHILD Or WS_BORDER             ,445 ,435 , 130, 25, hWnd, 0, 0, 0 )
COPY_OUTPUT_TO_INPUT = CreateWindowEx( 0,"BUTTON" ,  "Copy to Input", WS_VISIBLE Or WS_CHILD Or WS_BORDER    ,445 ,480 , 130, 25, hWnd, 0, 0, 0 )

HELP                 = CreateWindowEx( 0,"BUTTON"  , "Help"         , WS_VISIBLE Or WS_CHILD Or WS_BORDER,445 ,525 , 130, 25, hWnd, 0, 0, 0 )
'End Control setup

PrintKey()

'===============================================================================
'===============================================================================
'===============================================================================
'===============================================================================
'begin mesage processing
While GetMessage( @msg, 0, 0, 0 )
   
    dim as WPARAM wparam
    dim as LPARAM lparam
   
    TranslateMessage( @msg )
    DispatchMessage( @msg )
 
    Select Case msg.hwnd
        Case hWnd
            Select Case msg.message
                Case 273
                PostQuitMessage(0)
                'End
            End Select
         
        case TrackBar1
            Select Case msg.message
                case WM_MOUSEMOVE
                        trackpos1 = SendMessage(TrackBar1, TBM_GETPOS, 0, 0) *8
                        if trackpos1 <> getlast1 then
                            setwindowtext(MESSAGE_SIZE,Str(trackpos1))
                            MessageSize()
                            getlast1 = trackpos1
                        end if
            End Select
           
        case TrackBar2
            Select Case msg.message
                case WM_MOUSEMOVE
                        trackpos2 = SendMessage(TrackBar2, TBM_GETPOS, 0, 0) 
                        if trackpos2 <> getlast2 then
                            setwindowtext(GARBAGE_SIZE,Str(trackpos2))
                            GarbageSize()
                        end if
                        getlast2 = trackpos2
           End Select
 
        Case LOADCYPHTEXT_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    LoadCypheredText()
            End Select
       
        Case CYPHER_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    Cypher()
            End Select
       
        Case DECYPHER_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    DeCypher()
            End Select
       
        Case LOADKEY_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    LoadKey()
            End Select
       
        Case SAVEKEY_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    SaveKey()
            End Select
       
        Case HELP
            select case msg.message
                case WM_LBUTTONDOWN
                    MessageBox(0,Help_Text,"Help",MB_OK)
            end select
           
        Case SAVEOUTPUT_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    SaveOutput()
            End Select
       
        Case COPY_OUTPUT_TO_INPUT
            select Case msg.message
                case WM_LBUTTONDOWN
                    CopyOutputToInput()
            end select
       
        Case GENERATEKEY_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    GenerateKey()
            End Select
       
        Case GENERATESUBKEY_BTN
            Select Case msg.message
                case WM_LBUTTONDOWN
                    GenerateSubKey()
            End Select
   
    End Select

Wend
PostQuitMessage(0)
END
'===============================================================================
'===============================================================================
'subs and functions below here
'===============================================================================
'===============================================================================
sub MessageSize()
    dim as string*6 textin
    GetWindowText(MESSAGE_SIZE,textin,5)
    textin=trim(textin,chr(32))
    textin=trim(textin,chr(0))
    Keys_Spinner_val = val(textin)
    if Keys_Spinner_val > Keys_Spinner_Val_max = 1024 then
        Keys_Spinner_val = Keys_Spinner_val_max
    end if
    dim as string str1
    dim as integer dec1
    do
        str1=str(Keys_Spinner_val/8)
        dec1=instr(1,str1,".")
        if dec1<>0 then Keys_Spinner_val+=1
    loop until dec1 = 0
    SetWindowText(MESSAGE_SIZE,str(Keys_Spinner_val))
    TabPages = Keys_Spinner_val / 8
    Garbagebits = Garbage_Spinner_Val*8*Keys_Spinner_Val
    GarbageBytes = GarbageBits/8/Keys_Spinner_val
    Redim as integer Key(0 to (64*TabPages)-1)
    PrintKey()
end sub
'===============================================================================
'===============================================================================
sub GarbageSize()
    dim as string*6 textin
    GetWindowText(GARBAGE_SIZE,textin,5)
    textin=trim(textin,chr(32))
    textin=trim(textin,chr(0))
    Garbage_Spinner_val = val(textin)
    if Garbage_Spinner_val > Garbage_Spinner_val_max then
        Garbage_Spinner_val = Garbage_Spinner_val_max
    end if
    SetWindowText(GARBAGE_SIZE,str(Garbage_Spinner_val))
    TabPages = Keys_Spinner_val / 8
    Garbagebits = Garbage_Spinner_Val*8*Keys_Spinner_Val
    GarbageBytes = GarbageBits/8/Keys_Spinner_val
    Redim as integer Key(0 to (64*TabPages)-1)
    PrintKey()
end sub
'===============================================================================
'===============================================================================
sub PrintKey()
    dim as string KeyText
    dim as longint count = 1
    for a as longint = lbound(key) to ubound(Key)
        if a mod 8 = 0 then KeyText+=right("____" + str(count),4)+")"
        KeyText+=right("________"+str(key(a)),8)
        if a mod 8 = 7 then KeyText +=chr(13)+chr(10) : count+=1
    next
    SETWINDOWTEXT( EDITKEY , KeyText)
end sub
'===============================================================================
'===============================================================================
sub LoadCypheredText()
   
    'can only load ascii text files
   
    GetFileName()
    FileData=""
   
    if fileexists(file) then
       
        dim as string char
        open file for input as #1
            do
                line input #1 , char
                FileData = fileData + (char) + chr(13) + chr(10)
            loop until EOF(1)
        close #1
       
        FileData = left(FileData,len(FileData)-2)
        SetWindowText(EDIT_In,FileData)
       
        FileData=""
        file=""
    end if
   
end sub

'===============================================================================
'===============================================================================
sub Cypher()
    
    GetKeys()
    
    cls
    print " Cyphering..."
    
    'get message input from input edit_box into a string
    dim as string GetInputMessage
    dim as ulongint txtlen
    txtlen = (GetWindowTextLength(EDIT_IN)+1)
    GetInputMessage = string(txtlen,chr(0))
    GetWindowText(EDIT_IN , GetInputMessage, txtlen)
    GetInputMessage = trim(GetInputMessage,chr(0))
    
    'make input string an even number of Block sizes
    dim as string str1
    dim as single dec
    do
       str1=str( len(GetInputMessage) / (TabPages*8) )
        dec=instr(1,str1,".")
        if dec<>0 then GetInputMessage+="_"   'if message is not a multiple of (TabPages*8) characters
    loop until dec=0
   
    'turn message into binary
    dim as string BinaryMessageBlocks
    for a as ulongint = 1 to len(GetInputMessage) step 1
        BinaryMessageBlocks+= right("00000000" + bin( asc(mid(GetInputMessage,a,1)) ) ,8)
    next   
   
    'Create random garbage strings
    print
    print "Building 100 random strings.."
    print
    redim as string Array( 0 to 100)
    for a as ulongint = lbound(Array) to ubound(Array)
        print a ; "  " ;
        Dim as string Garbage = string(GarbageBits,"1")
        randomize
        for b as ulongint = 1 to GarbageBits - (GarbageBits\4)
            mid(Garbage,int(rnd*len(Garbage))+1,1) = "0"
        next
        Array(a) = Garbage
    next
    
    'stick user message bits (TabPages*64/TabPages) into random garbage of length GarbageBits
    print
    dim as string MessageBits
    dim as string RandomGarbage
    dim as string Accumulated
    dim as ulongint mods = len(BinaryMessageBlocks) \ 100
    for a as ulongint = 1 to len(BinaryMessageBlocks) step (64*TabPages)
        
        if a mod mods = 0 then print len(BinaryMessageBlocks) - a ; "  " ;
                
        MessageBits = mid(BinaryMessageBlocks,a, 64*tabPages)
        RandomGarbage = Array( int(rnd*ubound(Array)) )
        for insert as ulongint = lbound(Key) to ubound(Key)
            'mid(RandomGarbage,Key(insert),1) = mid(MessageBits,insert+1,1)
            RandomGarbage[Key(insert)-1] = MessageBits[insert]
        next
        Accumulated+=RandomGarbage
    next
    redim Array(0)
    MessageBits=""
    RandomGarbage=""
    GetInputMessage=""
    BinaryMessageBlocks=""
    
    print
    print
    print "Done Cyphering , Building output..."
    print
    print "length = " ; len(Accumulated)
    print "chars  = " ; len(Accumulated) / 4
    dim as string CypheredOutput = string((len(Accumulated)\4),chr(0))
    print "chars  = " ; len(CypheredOutput)
    print
    dim as ulongint place = 0 
    dim as ubyte value
    dim as ulongint mod_test = int(len(Accumulated)\100)
    dim as ulongint prnt = len(Accumulated)
    for a as ulongint = 0 to len(Accumulated)-1 step 4
        if a mod mod_test = 0 then print (prnt - a) ; "  " ;
        value = 0
        value+= (Accumulated[a+0]-48)*8
        value+= (Accumulated[a+1]-48)*4
        value+= (Accumulated[a+2]-48)*2
        value+= (Accumulated[a+3]-48)'*1
        CypheredOutput[place] = (SubKey(value))
        place+= 1
    next
    print
    print
    print "Writing " ; len(CypheredOutput) ; " chars to output..."
    SetWindowText(EDIT_OUT,CypheredOutput)
    CypheredOutput = ""
    Accumulated=""
    
    print
    print "!!~~Done Cyphering~~!!"
    
end sub
'===============================================================================
'===============================================================================
sub DeCypher()
   
    GetKeys()
    
    cls
    print "Decyphering..."
    'get message input from input edit_box into a string
    dim as string GetInputMessage
    dim as ulongint txtlen
    txtlen = (GetWindowTextLength(EDIT_IN)+1)
    GetInputMessage = string(txtlen,chr(0))
    GetWindowText(EDIT_IN , GetInputMessage, txtlen)
    GetInputMessage = trim(GetInputMessage,chr(0))
   
    if len(GetInputMessage)<>0 then
       
        dim as string BinarySubOutput(1 to (len(GetInputMessage)/(GarbageBits/8)/2) )
        dim as string Bites
        dim as ulongint Chunks = (len(GetInputMessage)/(GarbageBits/8)/2)
        dim as ubyte Char
        Dim as ulongint Dec = 1
        for a as integer = 1 to len(GetInputMessage) step (len(GetInputMessage)/Chunks)
            Bites = mid( GetInputMessage, a, len(GetInputMessage)/Chunks )
            for b as integer = 1 to len(bites)
                Char = asc( mid(Bites,b,1) )
                for c as integer = 0 to 15
                    if Char = SubKey(c) then BinarySubOutput(Dec)+=right("0000"+bin(c),4)
                next
            next
            Dec+=1
        next
       
        Dec-=1
        dim as string Binary_out
        for a as integer = 1 to Dec step 1
            for b as integer = 0 to ubound(Key)
                Binary_Out+= mid(BinarySubOutput(a),Key(b),1)
            next
        next
       
        dim as string FinalOutput
        dim as string*8 OctaBits
        dim as ulongint mods = len(Binary_Out) \ 100
        for a as ulongint = 1 to len(Binary_Out) step 8
            
            if (a-1) mod mods = 0 then print len(Binary_out) - a ; "  " ;
            
            OctaBits = mid(Binary_Out,a,8)
            'mid(Binary_Out,a,8)="00000000"
            Dec=0
            if (OctaBits[0]-48) = 1 then Dec+=128
            if (OctaBits[1]-48) = 1 then Dec+= 64
            if (OctaBits[2]-48) = 1 then Dec+= 32
            if (OctaBits[3]-48) = 1 then Dec+= 16
            if (OctaBits[4]-48) = 1 then Dec+=  8
            if (OctaBits[5]-48) = 1 then Dec+=  4
            if (OctaBits[6]-48) = 1 then Dec+=  2
            if (OctaBits[7]-48) = 1 then Dec+=  1
       
            FinalOutput+=Chr(Dec)
        next
        print
        print "Done decyphering..."
        print
        print "Writing " ; len(FinalOutput) ; "chars to output..."
        FinalOutput = rtrim(FinalOutput,"_")
        SetWindowText(EDIT_OUT,FinalOutput)
        print
        print "!!~~Done decyphering~~!!"
    end if
   
end sub
'===============================================================================
'===============================================================================
sub GetKeys()
   
    dim as string*1 CharSubKey
    for a as integer = 1 to 2
        for b as integer = 1 to 8
            'print ((a*8)-8) +b-1
            GetWindowText( EDIT_OUTS( ((a*8)-8)+b-1 ) , CharSubKey , 2)
            SubKey( ((a*8)-8)+b-1 ) = asc(CharSubKey)
        next
    next
   
end sub
'===============================================================================
'===============================================================================
sub LoadKey()
   
    GetFileName()
   
    if fileexists(file) then
       
        open file for input as #1
           
            dim as String Inputs
           
            line input #1 , Inputs
            SetWindowText(MESSAGE_SIZE,Inputs)
            Keys_Spinner_Val = val(inputs)
            MessageSize()
            SendMessage( TrackBar1 , TBM_SETPOS,1, val(inputs)\8)
            getlast1 = SendMessage(TrackBar1, TBM_GETPOS, 0, 0) *8
            
            line input #1 , Inputs
            SetWindowText(GARBAGE_SIZE,Inputs)
            Garbage_spinner_val = val(inputs)
            GarbageSize()
            SendMessage( TrackBar2 , TBM_SETPOS,1, val(inputs))
            getlast2 = SendMessage(TrackBar2, TBM_GETPOS, 0, 0) 
            
            Redim Key(0 to Keys_Spinner_val*8-1)
            Redim SubKey(0 to 15)

            dim as ulongint count
           
            count=0
            do
                line input #1 , Inputs
                Key(count) = val(Inputs)
                count+=1
            loop until count > ubound(Key)
           
            count=0
            do
                line input #1 , Inputs
                SubKey(count) = val(Inputs)
                count+=1
            loop until count = 16
           
        Close #1
       
        PrintKey()
       
        dim as integer dec
        for y as integer = 1 to 2 step 1
            for x as integer = 1 to 8 step 1
                Dec = (((y*8)-8)+x)-1
                'print y,x,Dec,SubKey(Dec)
                SetWindowText(EDIT_OUTS( Dec ) , chr(SubKey(Dec)) )
            next
        next
           
        file=""
        extension=""

    end if
   
end sub
'===============================================================================
'===============================================================================
sub SaveKey()
   
    getkeys()
   
    GetFileName()
   
    dim as string SaveKeys = ""
   
    if file<>"" then
   
        open file for output as #1
           
            dim as string*6 textin
            GetWindowText(MESSAGE_SIZE,textin,5)
            print #1 , textin
           
            GetWindowText(GARBAGE_SIZE,textin,5)
            print #1 , textin
           
            for a as integer = lbound(key) to ubound(key)
                print #1 , str(Key(a))
            next
       
            for a as integer = 0 to 15
                Print #1 , SubKey(a)
            next
       
        close #1
   
    end if
   
end sub
'===============================================================================
'===============================================================================
sub SaveOutput()
   
    GetFileName()
    if file<>"" then
       
        'get message input from Output edit_box into a string
        dim as string GetOutputMessage
        dim as integer txtlen
        txtlen = (GetWindowTextLength(EDIT_OUT)+1)
        GetOutputMessage = string(txtlen,chr(0))
        GetWindowText(EDIT_OUT , GetOutputMessage, txtlen)
        GetOutputMessage = trim(GetOutputMessage,chr(0))

        open file for output as #1
       
            print #1 , GetOutputMessage
       
        close #1
   
    end if
   
end sub
'===============================================================================
'===============================================================================
Sub CopyOutputToInput()
        'get message input from Output edit_box into a string
        cls
        print "Preparing to copy..."
        dim as string GetOutputMessage
        dim as integer txtlen
        txtlen = (GetWindowTextLength(EDIT_OUT)+1)
        GetOutputMessage = string(txtlen,chr(0))
        GetWindowText(EDIT_OUT , GetOutputMessage, txtlen)
        GetOutputMessage = trim(GetOutputMessage,chr(0))
        print
        print "Copying " ; len(GetOutputMessage) ; " chars to input..."
        SetWindowText(EDIT_IN , GetOutputMessage)
        print
        print "!!~~Done Copying~~!!"
end sub
'===============================================================================
'===============================================================================
sub GenerateKey()
    ' ((a*64)-64)+((x*8)-8)+y
    Redim Key(0 to (TabPages*64-1) )
       
    dim a as integer
    dim b as integer
    dim c as integer
    dim d as integer
 
    'create random key for main cypher.
    for a = 0 to (TabPages*64)-1
        key(a) = 0
    next
     
    a=0
    do
        do
            randomize
            b = int(rnd*GarbageBits)+1
            d = 0
            for c = 0 to a
               if key(c) = b then d = 1
            next
        loop until d = 0
        key(a) = b
        a = a + 1     
    loop until a=(TabPages*64)     

    PrintKey()
       
end sub
'===============================================================================
'===============================================================================
sub GenerateSubKey()
     
    Redim SubKey(0 to 15)
    'create 16 letter subsitution for output
    dim a as integer
    dim b as integer
    dim c as integer
    dim d as integer
     
    for a = 0 to 15
        SubKey(a) = 0
    next
    a = 0
    do
        do
            do
                randomize
                b = int( rnd * 256 )
                if b >= 65 and b <= 90 then exit do
                if b >= 97 and b <= 122 then exit do
            loop
            d = 0
            for c = 0 to a
                if SubKey(c) = b then d = 1
            next
        loop until d = 0
        SubKey(a) = b
        a = a + 1     
    loop until a = 16
     
    'answer = ((a*8)-8) +b
    for a = 1 to 2
        for b = 1 to 8
            'print ((a*8)-8) +b-1
            SetWindowText( EDIT_OUTS( ((a*8)-8)+b-1 ) , chr( SubKey( ((a*8)-8)+b-1 ) ) )
        next
    next
   
end sub

'===============================================================================
'===============================================================================
sub getfilename()
        dim ofn as OPENFILENAME
        dim filename as zstring * MAX_PATH+1
       
        with ofn
                .lStructSize            = sizeof( OPENFILENAME )
                .hwndOwner              = hWnd
                .hInstance              = GetModuleHandle( NULL )
                .lpstrFilter            = strptr( !"All Files, (*.*)\0*.*\0\0" )
                .lpstrCustomFilter      = NULL
                .nMaxCustFilter         = 0
                .nFilterIndex           = 1
                .lpstrFile              = @filename
                .nMaxFile               = sizeof( filename )
                .lpstrFileTitle         = NULL
                .nMaxFileTitle          = 0
                .lpstrInitialDir        = NULL
                .lpstrTitle             = @"File To Open."
                .Flags                  = OFN_EXPLORER 'or OFN_FILEMUSTEXIST or OFN_PATHMUSTEXIST
                .nFileOffset            = 0
                .nFileExtension         = 0
                .lpstrDefExt            = NULL
                .lCustData              = 0
                .lpfnHook               = NULL
                .lpTemplateName         = NULL
        end with
       
        if( GetOpenFileName( @ofn ) = FALSE ) then
            file = ""
            extension=""
            return
        else
            file = filename
            extension = right$(filename,4)
        end if

end sub

---

