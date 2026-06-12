---
title: "PHP Toy Project Gone South"
date: 2016-03-31
forum: Programming Talk
---

### Post by Steve_Corenflos on 2016-03-31
I'm trying to figure out where I went wrong with a toy project I'm working on. It's just a Hangman implementation, but whether it's lack of sleep or losing my touch I somehow have gotten myself stuck, and if someone could help get me unstuck I would greatly appreciate it.

I can't get the game classes to properly interface with the index page. For some reason submitting POST forms is not giving me a POST global on the other side. Please take pity on me and help me with this. It's driving me crazy today. Thanks for any help!

index.php
[PHP]<?php//include the required files
require_once('src/Hangman.php');
require_once('src/WordList.php');

//this will keep the game data as they refresh the page
session_start();

//load a game if one hasn't started yet
if (!isset($_SESSION['game']['hangman'])) {
    $_SESSION['game']['hangman'] = new \demo\src\Hangman();
    $game = $_SESSION['game']['hangman'];
}

if (isset($_POST['letter'])) {
    $game->guess($_POST['letter']);
    echo "GRRARGH!" . $game->maskedWord;
}

print_r($_POST);
print_r($_SESSION);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hangman Demo</title>
    <link rel="stylesheet" type="text/css" href="css/style.css" />
</head>
<body>
<div class="wrapper">
<div class="header"><h1>Let's Play Hangman!</h1></div>
<div class="left">
    <canvas id="gallows" width="400" height="200" style="border:1px solid #000000;">
        <p>Your browser doesn't support canvas.</p>
    </canvas>
</div>
<div class="right">
    <div class="game">
        Word: <?= implode(" ", $_SESSION['game']['hangman']->maskedWord); ?>
    </div>

    <div class="game">
        <form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post">
            <label for="letter">Guess a letter:</label>
            <input type="text" name="letter" id="letter" size="2" maxlength="1" />
            <input type="submit" name="guess" />
        </form>
    </div>

    <div class="game">
        Your Guesses: <br />
        <?= implode(", ", $_SESSION['game']['hangman']->guessedLetters); ?>
    </div>
</div>
<div class="footer">
</div>
</div>


</body>
</html>[/PHP]

Hangman.php
[PHP]<?phpnamespace demo\src;


class Hangman
{
    public $targetWord;
    public $maskedWord = array();
    const NUM_GUESSES = 6;
    public $guesses;
    public $guessedLetters = array();
    public $gameOver = false;

    public function __construct($word = null) {
        $this->newGame($word);
    }

    public function newGame($word = null) {
        // can be passed a word to start, or get a random one from the word list
        if (is_null($word)) {
            $wordList = new WordList;
            $this->targetWord = $wordList->getRandomWord();
        } else {
            $this->targetWord = $word;
        }
        // set the masked word
        $this->maskedWord = str_split(str_repeat("_",strlen($this->targetWord)));

        // reset guesses and gameOver
        $this->guesses = Hangman::NUM_GUESSES;
        $this->gameOver = false;
    }

    public function nextRound($letter) {
        if (($this->guesses == 0) || ($this->targetWord == implode($this->maskedWord))) {
            $this->gameOver = true;
        } else {
            $this->guess($letter);
        }
    }

    public function guess($letter) {

        if ($this->isOver())
            return;

        $hit = 0;
        for ($i=0; $i<strlen($this->targetWord); $i++) {
            if ($this->targetWord{$i} == $letter) {
                $hit++;
                $this->maskedWord[$i] = $letter;
            }
        }
        if ($hit == 0) {
            if ($this->guesses == 0) {
                $this->gameOver = true;
            } else {
                array_push($this->guessedLetters, $letter);
                $this->guesses -= 1;
            }
        }

    }

    function isOver()
    {
        if ($this->gameOver)
            return true;

        if ($this->guesses == 0)
            return true;

        return false;
    }


}[/PHP]

WordList.php
[PHP]<?phpnamespace demo\src;


class WordList
{
    const DEFAULT_WORDLIST = array("word", "list", "missing");
//    const DEFAULT_PATH = 'data/words.txt';
    private $path = 'data/words.txt';
    private $wordList = null;


    public function __construct($wordListPath = null) {
        $this->wordList = (is_null($wordListPath)) ? file($this->path) : file($wordListPath);
    }

    public function getRandomWord() {
        $randomKey = array_rand($this->wordList, 1);
        return $this->wordList[$randomKey];
    }

}[/PHP]

---

### Post by Steve_Corenflos on 2016-04-01
Ok, first problem seems to be that there's some kind of configuration issue with my Apache server/PHP setup. The same script passes the form values to the receiving side's $_POST variable just fine on a different server. But for some reason it's not on my server.

---

### Post by spjackson on 2016-04-01
> 
```

[COLOR=#000000][COLOR=#007700]    const [/COLOR][COLOR=#0000BB]DEFAULT_WORDLIST [/COLOR][COLOR=#007700]= array([/COLOR][COLOR=#DD0000]"word"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]"list"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]"missing"[/COLOR][COLOR=#007700]);
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

Which php version is this? The above line gives me (on php 5.5):
```

PHP Fatal error:  Arrays are not allowed in class constants in /var/www/html/demo/src/WordList.php on line 7

```

---

