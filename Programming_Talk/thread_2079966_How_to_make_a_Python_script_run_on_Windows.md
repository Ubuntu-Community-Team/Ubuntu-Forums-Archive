---
title: "How to make a Python script run on Windows?"
date: 2012-11-02
forum: Programming Talk
---

### Post by Stovey on 2012-11-02
Hi.  I wrote my first real Python program over the last week, and now I would like to package it to run on Windows.  Would someone kindly explain how this is done?

The program takes a list of urls in a text file, searches the websites according to a regular expression, and then prints the result to excel.  Also, there are two modules: the first does the work, and the second is a GUI.

The program is written with Python3.2 uses the following modules: urllib.request, re, win32com.client, pickle, os and tkinter.

Thanks.

---

### Post by Stovey on 2012-11-03
I am going to try to use cx_Freeze.  Here are my scripts, the first does the real work and the second is the GUI.  Any comments are welcome:

```
#!/usr/bin/python3.2
# dostats.py version: 1.2
#
# V1.2 adds an HTML class
# V1.3 "search and replace" allows multiple searches
#
# This program creates a list of players from a text file, and a list
# of urls from another text files.  The websites are then searched for
# player names, and the stats for each player are recorded.  Stats
# are then written to an excel spreadsheet.

import urllib.request
import re
from win32com.client import Dispatch
import pickle
import os

let_to_num = {'A': 1, 'B': 2, 'C': 3, 'D': 4, 'E': 5, 'F': 6, 'G': 7,
              'H': 8, 'I': 9, 'J': 10, 'K': 11, 'L': 12, 'M': 13, 'N': 14,
              'O': 15, 'P': 16, 'Q': 17, 'R': 18, 'S': 19, 'T': 20, 'U': 21,
              'V': 22, 'W': 23, 'X': 24, 'Y': 25, 'Z': 26}
spreadsheet = os.path.join(os.getcwd(), 'test.xlsx')
player_filename = "player_list.txt"
url_filename = "urls.txt"

class Player:
    """A player is an object representing the member of a team.
    Instance variables representing the player include name & position.
    Stats and stat_cells are corresponding tuples that contain the stats
    and the cells of the spreadsheet to write those stats.  Other data
    for use in updating the stats and writing to a spreadsheet include regex
    (regular expression for extracting the data), spreadsheet name,
    and worksheet name."""

    all_players = [] # keep a list of all players created
    
    def __init__(self, name):
        """Creates a player, eg:
        skater = Player("Alex Ovechkin")"""
        self.name = name
        self.regex = ""
        self.worksheet = ""
        self.stats = ""
        self.stat_cells = ""
        self.__class__.all_players.append(self)

    def __str__(self):
        return self.name

    def get_stats(self, html): # gets stats for each player from html
        regex_string = self.name + self.regex
        reg_ex = re.compile(regex_string)
        search_object = reg_ex.search(html.string)
        if search_object is not None:
            self.stats = search_object.groups()
            start, end = search_object.start(), search_object.end()
            html.string = html.string[:start] + html.string[end:]

    def print_report(self):
        print(self.name)
        print(self.stats)
        print(self.stat_cells)
        print(self.regex)
        print(self.worksheet)

class HTML:
    """HTML is a single string of source code built from URLs given
    by the URL text file.  Once built, the HTML string may be saved to file
    and then loaded (with the advantage of speed and "bot" like calls
    to websites while testing).  HTML string may be searched, and once found the
    search string may be replaced."""

    def __init__(self):
        self.string = ""

    def build(self, url_list): # build single string from all html sourcecode
        for url in url_list:
            response = urllib.request.urlopen(url)
            self.string = self.string + str(response.read())
            response.close()

    def load(self):
        file = open("state", 'rb')
        self.string = pickle.load(file)
        file.close()

    def save(self):
        file = open("state", 'wb')
        pickle.dump(self.string, file)
        file.close()

def load_players(): # create players from file, including spreadsheet data
    player_file = open(player_filename, 'r')
    for line in player_file:
        line_list = line.rstrip().split('\t')
        if len(line_list) == 1: # check if line specifies worksheet or regex
            if line_list[0].startswith("regex"):
                regex = line[7:].rstrip()
            else:
                xl_worksheet = line_list[0]
        else: # line must be a player, create a player object
            player_object = Player(line_list[0])
            player_object.worksheet = xl_worksheet
            player_object.regex = regex
            player_object.stat_cells = line_list[1:]
            
def get_urls(): # build list of urls from text file
    url_file = open(url_filename, 'r')
    url_list = []
    for each_line in url_file:
        url_list.append(each_line)
    url_file.close()
    return url_list

def open_excel():
    excel = Dispatch('Excel.Application')
    excel.Visible = True
    workbook = excel.Workbooks.Open(spreadsheet)
    return workbook

def update_excel(player, workbook):
    count = 0
    for cell in player.stat_cells:
        col, row = cell_to_num(cell)
        sheet = workbook.Sheets(player.worksheet)
        sheet.Cells(row, col).Value = (player.stats[count])
        count = count + 1

def cell_to_num(cell): # convert excel cell notation ie B7 to number ie 2, 7
    col = ""
    split_cell = list(cell)
    for i in split_cell:
        if not i.isdigit():
            col = col + i
            split_cell = split_cell[1:]
    row = "".join(split_cell)
    col = col_to_num(col)
    return int(col), int(row)

def col_to_num(col): # convert letter for excel column ie A or AA to number
    if len(col) == 1:
        col = let_to_num[col.upper()]
    else:
        col = (let_to_num[col[0].upper()] * 26) + let_to_num[col[1].upper()]
    return col

def set_spreadsheet():
    global spreadsheet
    spreadsheet = input("Please enter spreadsheet filename: ")
    spreadsheet = os.path.join(os.getcwd(), spreadsheet)

def set_pfilename():
    global player_filename
    player_filename = input("Please enter player filename: ")

def set_ufilename():
    global url_filename
    url_filename = input("Please enter url filename: ")
            
def main():
    load_players()
    url_list = get_urls()
    html = HTML()
    # html.build(url_list)
    html.load()
    workbook = open_excel()
    for player in Player.all_players:
        player.get_stats(html)
        update_excel(player, workbook)

if __name__ == 'main': main()
```

```
# dostats_gui.py
#
# This "drives" the dostats.py program
# with a simple Tkinter interface.

import dostats
from tkinter import *
from tkinter import filedialog
import os

class App:

    def __init__(self, master):
        master.wm_title('Do Stats')
        master.wm_iconbitmap('icon.ico')
        frame = Frame(master)
        frame.pack()

        self.sfile_label = Label(frame, text="Spreadsheet: ",
                                 width='14', anchor='e')
        self.sfile_label.grid(row=0, column=0)
        sfile = os.path.basename(dostats.spreadsheet)
        self.sfile_but = Button(frame, text=sfile,
                                command=lambda b='sht': self.set_filename(b))
        self.sfile_but.grid(row=0, column=1)

        self.pfile_label = Label(frame, text="Players: ",
                                 width='14', anchor='e')
        self.pfile_label.grid(row=1, column=0)
        self.pfile_but = Button(frame, text=dostats.player_filename,
                                command=lambda b='plyr': self.set_filename(b))
        self.pfile_but.grid(row=1, column=1)

        self.ufile_label = Label(frame, text="URLs: ",
                                 width='14', anchor='e')
        self.ufile_label.grid(row=2, column=0)
        self.ufile_but = Button(frame, text=dostats.url_filename,
                                command=lambda b='url': self.set_filename(b))
        self.ufile_but.grid(row=2, column=1)

        self.stats_but = Button(frame, text="Do Stats", command=dostats.main)
        self.stats_but.grid(row=3, column=1)

    def set_filename(self, b):
        filename = filedialog.askopenfilename()
        if b == "url":
            dostats.url_filename = filename
            self.ufile_but['text'] = os.path.basename(filename)
        elif b == "plyr":
            dostats.player_filename = filename
            self.pfile_but['text'] = os.path.basename(filename)
        else:
            dostats.spreadsheet = filename
            self.sfile_but['text'] = os.path.basename(filename)
            

root = Tk()

app = App(root)

root.mainloop()
```

---

### Post by cybergalvez on 2012-11-03
you might want to check out [http://www.py2exe.org/](http://www.py2exe.org/)

---

### Post by Stovey on 2012-11-05
Thanks.  I looked at p2exe but it seems it is not yet ready for Python3.

cx_freeze was somewhat successful, but the setup file didn't want to recognize the directories in which my files were stored.

So I gave it an absolute file path for the executable, and copied the dependent files manually.

---

