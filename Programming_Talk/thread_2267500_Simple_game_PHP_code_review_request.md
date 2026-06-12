---
title: "Simple game PHP code review request"
date: 2015-03-02
forum: Programming Talk
---

### Post by NeooeN on 2015-03-02
Hi!
I have written a simple game of sokoban in php and I would like to ask for a comment on my code. The very first thing to say is that it is a cli script and all starts with main.php.


[php]<?php
system("stty -icanon");          //this line will cause php to recive every single character typed into terminal without                                 //pressing enter, it is not the best way of doing this and limits usage of this program                                 //to linux but it works
include "sokoban.php";           //this file contains class handling the game logicinclude "cliClass.php";          //this file contains class extending sokoban class and adding draw functioninclude "mapFromBase.php";       //definition of a single function that converts maps from string format to one that                                 //sokoban class uses
$game = new cliClass();          //declare a new sokoban object (cliClass is child of sokoban)$game->loadMap(mapFromBase("BggEBgYGCQkGCQkQAAAAAKiqqip4VVUtWFVVJVhVVSVYVVUlWFVVJViVViVYlVYlWFVVJVhVVSVYVVUlWFVVJXhVVS2oqqoqAAAAAA=="));
echo $game->draw();              //lets print the first "frame" of the game
$moves = array (); $moves["w"] = 0; $moves["a"] = 3; $moves["s"] = 1; $moves["d"] = 2;//just an auxiliary array
while ($c = fread(STDIN, 1)) {   //iterate through all keys pressed by the user    if ("w" == $c || "a" == $c || "s" == $c || "d" == $c) {//filter out anything but WASD        $game->move($moves[$c]); //invoke move method with proper param        echo $game->draw();      //and print next frame        if ($game->check()) break;    }}
?>[/php]


It starts with a game initialization ("new cliClass()") and map loading ("$game->loadMap()"). Then we have a simple loop over upcoming datas, that processes them and passes to game object ("$game->move()"). The whole file is just to make the actual code running.


The sokoban.php contains sokoban class that has following public methods:



[LIST]
[*]loadMap - as a parameter it takes an array of complex format
[*]move - takes one integer of range 0-3 which means movements done by player (up, down, left, right)
[*]check - checks if all "stones" stands on an "X" field (the goal of the game) and returns bool accordingly
[/LIST]



and is listed below:


[php]<?php
  class sokoban {
    const stop = 0;       const freeToGo = 1;       const moveStone = 2;
    public $map = array ();    //0 - void    //1 - floor    //2 - wall    //3 - X    public $stones = array ();    public $player = array ();    protected $moveDirection;    //0 - array (-1, 0)    //1 - array (1, 0)    //2 - array (0, 1)    //3 - array (0, -1)        function loadMap ($map = array ()) {      foreach ($map[2] as $rowId => $row) {  //mapa        foreach ($row as $fieldId => $field) {          if ($field < 0 || $field > 3) throw new exception ("Z&#322;a warto&#347;&#263; w array'u mapy (\$rowId = $rowId ; \$fieldId = $fieldId)!");          $this->map [$rowId][$fieldId] = $field;        }      }      foreach ($map[1] as $stone) { //kamienie        $this->stones[] = $stone;      }      $this->player = $map[0];      return $this;    }        function move ($moveDirection) {      $this->moveDirection = $moveDirection;      if ($this->isFree ()) {        $this->player = $this->translateMoveDirection ();      }      foreach ($this->stones as &$stone) {        if ($stone[0] == $this->player[0] && $stone[1] == $this->player[1]) {          $stone = $this->translateMoveDirection ();        }      }    }
    function translateMoveDirection ($r = null) {          return array ($this->player[0] + ($this->moveDirection == 1 ?                                                                   (isset ($r) ?                                                                                2 :                                                                                1                                                                   ) :                                                                   ($this->moveDirection == 0 ?                                                                                               (isset ($r) ?                                                                                                            -2 :                                                                                                            -1                                                                                               ) :                                                                                               0                                                                   )                                       ),                    $this->player[1] + ($this->moveDirection == 2 ?                                                                   (isset ($r) ?                                                                                2 :                                                                                1                                                                   ):                                                                   ($this->moveDirection == 3 ?                                                                                               (isset ($r) ?                                                                                                            -2 :                                                                                                            -1                                                                                               ) :                                                                                               0                                                                   )                                       )                   );    }
    function isFree ($r = null) {        $x = $this->translateMoveDirection ($r)[0];        $y = $this->translateMoveDirection ($r)[1];      if ($this->map [$x][$y] == 2) {        return false;      }      foreach ($this->stones as $stone) {        if ($stone[0] == $x && $stone[1] == $y) {             return (isset($r) ?                             false :                             $this->isFree (1)                 );        }      }      return true;    }        public function check () {      foreach ($this->stones as $stone) {        if (!($this->map[$stone[0]][$stone[1]] == 3)) {          return false;        }      }      return true;    }
  }
?>[/php]


The move method invokes isFree, which checks if the player is trying to stand on a wall (which is forbidden) or if is trying to push two stones at once (forbidden as well). Both move and isFree methods invokes translateMoveDirection which is doing simple calculations to determine position of processed elements.


My first concerns concern the algorithm of move method and those invoked by it. The move method saves its parameter in a class field instead of passing it to invoked methods. This is due to the fact that I was trying to save memory (every invoked method uses this parameter so passing it all the time would cause the interpreter to copy the parameter a few times for no reason, in my way it is stored in a field once). Is it worth it or should the invoked methods (isFree, translateMoveDirection) takes the data as a parameter?


Another thing is it worth to make translateMoveDirection static, since it would return the value based only on the parameter not on an object internal state? My general question (at least on that file) is: is it possible to make it more object oriented, to simplify the whole? I was wondering if it would be possible to somehow break it to separated classes representing game, map and stones?


The next file is cliClass.php:


[php]<?php
  require_once "sokoban.php";
  class cliClass extends sokoban {
    function draw () {      $obj = array ();      $drawing = array ();      foreach ($this->map as $map) {        $drawing[] = "";        foreach ($map as $m) {          switch ($m) {            case 0: $drawing[count($drawing)-1] .= ".";              break;            case 1: $drawing[count($drawing)-1] .= " ";              break;            case 2: $drawing[count($drawing)-1] .= "W";              break;            case 3: $drawing[count($drawing)-1] .= "X";              break;          }        }      }      foreach ($this->stones as $stone) {        @$drawing[$stone[0]][$stone[1]] = "O";      }      $drawing[$this->player[0]][$this->player[1]] = "|";      $toReturn = "";      foreach ($drawing as $d) {        $toReturn .= $d."\n";      }      return $toReturn;    }
  }
?>[/php]


There is no much to say, it's basically a class extending sokoban class and adding draw method, that is returning a string that printed to a terminal represents a game "frame". It is more for debugging purposes but I would like to ask if this way of adding functionalities to existing classes is a good way to do OOP?


And the last file is mapFromBase.php:


[php]<?php
  function mapFromBase ($text) {    $text = str_split (base64_decode($text));    foreach ($text as &$char) {      $char = ord ($char);    }    $player = array (array_shift ($text), array_shift ($text));    $stones = array ();    for ($i = array_shift ($text); $i != 0; $i--) {      $stones[] = array (array_shift ($text), array_shift ($text));    }    $map = array ();    $line = array ();    $wrap = array_shift ($text);    foreach ($text as $byte) {      for ($j = 0; $j < 4; $j++) {        $line[] = ($byte & (3 << $j*2)) >> ($j*2);        if (count ($line) == $wrap) {          $map[] = $line;          $line = array ();        }      }    }    if (count ($line) != 0) {      $map[] = $line;    }    return array ($player, $stones, $map);  }    //print_r (mapFromBase ("BggEBgYGCQkGCQkQAAAAAKiqqip4VVUtWFVVJVhVVSVYVVUlWFVVJViVViVYlVYlWFVVJVhVVSVYVVUlWFVVJXhVVS2oqqoqAAAAAA=="));
?>[/php]


It stores a single function mapFromBase that is used to convert from one (string) format to another (array) datas about map (shape of the walls, stones, X's) and I have no idea how to do it properly. I would like my code to be prepared to create more formats and also keep it independent from the cliClass. I guess I have to use some pattern like factory or builder, but I am really confused by the choice so I ask for any advice on that as well.


In general I ask for any advices and comments on what can be done to make my code being better quality. I'll be very grateful for any help!

BTW. I can see that code formatting gets messy on this forum. Am I doing this wrong? Maybe on [this]("http://www.codingforums.com/php/337027-simple-game-code-review-request.html#post1436770") forum it will be more clear.

---

