Download Link: https://assignmentchef.com/product/solved-cse-231-computer-project-10
<br>
<strong>Assignment Overview </strong>

<strong> </strong>This assignment focuses on the design, implementation and testing of a Python program which uses an instructor-supplied module to play a card game, as described below.




It is worth 60 points (6% of course grade) and must be completed no later than 11:59 PM on Thursday, <strong>April 16, 2020</strong>.




<strong>Assignment Deliverables </strong>




The deliverable for this assignment is the following file:




<strong>proj10.py</strong> – the source code for your Python program




Be sure to use the specified file name and to submit it for grading via the <strong>Mimir</strong> <strong>system</strong> before the project deadline.




<strong>Assignment Background </strong>

<strong> </strong>

Aces Up is a popular solitaire card game which is played by one person with a standard 52-card deck of cards.  The rules and a tutorial video are available at:




<a href="http://worldofsolitaire.com/">http://worldofsolitaire.com/</a>




Click on “Choose Game” at the top of the screen and click on “Montana”.




Your program will allow the user to play the game Montana, with the program managing the game.  The game rules are given below.




<strong>Game Rules</strong>




<ol>

 <li>Start: The game is played with one standard deck of 52 cards with aces removed (so there are 48 cards). The deck is shuffled, and all 48 cards are dealt face up into a <em>tableau</em> of four rows of thirteen places each.  When the 48 cards are dealt there will be four empty spaces.</li>

</ol>




Montana Solitaire.

<ul>

 <li>2 3   4   5   6   7   8   9  10  11  12  13</li>

</ul>

1:  4&#x2663;  2&#x2660;  6&#x2666;  9&#x2663;      2&#x2663;  7&#x2665;  9&#x2660;  4&#x2665;  7&#x2663;  4&#x2660;  7&#x2660;

2:  6&#x2663;  2&#x2665; 10&#x2660;  6&#x2665;  4&#x2666;  K&#x2666;  8&#x2660;  8&#x2665;  2&#x2666;  K&#x2665;  5&#x2663;  J&#x2665;  9&#x2665;

3:  5&#x2666;  Q&#x2665;      K&#x2663;  7&#x2666;  3&#x2660;  3&#x2665;  5&#x2660;  9&#x2666;  J&#x2660; 10&#x2663;  K&#x2660;  8&#x2663;

4:  3&#x2663;  Q&#x2666;  J&#x2666;  6&#x2660;      8&#x2666;  5&#x2665;  J&#x2663;  Q&#x2660;  Q&#x2663;  3&#x2666; 10&#x2666; 10&#x2665; (Implementation note: we won’t actually remove the aces from the deck.  Instead we use the aces as the place holders for the blank spaces.  When we display the cards we don’t display anything for an ace so it shows up as an empty space.  Also, when we check whether a space is empty or has a card we can check whether the place in the tableau has an ace.)




Most solitaire games also have a <em>stock</em> and a <em>foundation</em> but not this game.




<ol start="2">

 <li>Goal: The game is won when each row of the tableau is an increasing sequence of cards of the same suit starting with a 2 in the leftmost column up through a king in the next to last column with a blank space in the rightmost column (actually holding an ace that isn’t displayed, but the ace may be of any suit since it is simply representing a blank space). Note that any suit may be in any row, but the entire row must be of the same suit.</li>

</ol>




<ol start="3">

 <li>Moves: A player can move only one card at a time and only to an empty space.  A move is valid only if the card to the left of the empty space is the same suit and one less in rank than the card being moved.</li>

</ol>




<ol start="4">

 <li>Shuffle: (Note that this is the hardest part of the game and should only be implemented after the rest of the game is complete.)  Only some cards are shuffled: cards that are already in a samesuit sequence starting with a 2 in the leftmost column are left in place and not shuffled.  All other cards are shuffled and then dealt back into the tableau, but there will be one blank space in each row and it will be at the right end of the sequence that is left in place (or in the leftmost column, if there is no sequence in that row).</li>

</ol>




Before shuffle with sequences highlighted in red




<ul>

 <li>2 3   4   5   6   7   8   9  10  11  12  13</li>

</ul>

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;      Q&#x2663;  J&#x2660;  9&#x2660;  8&#x2660; 10&#x2665;  6&#x2660;  8&#x2663;

2:      2&#x2660;  3&#x2660;  4&#x2660;  8&#x2665;  4&#x2665;  7&#x2665;  6&#x2665;  9&#x2663; 10&#x2666;  K&#x2665;  Q&#x2665;  J&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  9&#x2666;  Q&#x2660;  5&#x2665;      K&#x2663;      J&#x2666;

4:  2&#x2665;  J&#x2665;  8&#x2666;  Q&#x2666;  K&#x2660; 10&#x2663;  3&#x2665;  7&#x2660;  7&#x2663; 10&#x2660;  K&#x2666;  9&#x2665;  5&#x2660;




After shuffle with sequences highlighted in red.  Note the blank space to the right of each sequence (and in the leftmost column for a row with no sequence).




1   2   3   4   5   6   7   8   9  10  11  12  13    1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;      8&#x2665;  3&#x2665;  9&#x2660;  4&#x2665; 10&#x2663;  2&#x2660;  7&#x2665;

2:      5&#x2660;  5&#x2665;  6&#x2665; 10&#x2666;  Q&#x2666;  Q&#x2663;  8&#x2663;  8&#x2666;  K&#x2666;  J&#x2665;  K&#x2660; 10&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;      K&#x2665;  J&#x2660; 10&#x2660;  J&#x2666;  Q&#x2665;  K&#x2663;

4:  2&#x2665;      Q&#x2660;  7&#x2663;  3&#x2660;  9&#x2665;  4&#x2660;  6&#x2660;  J&#x2663;  9&#x2663;  8&#x2660;  7&#x2660;  9&#x2666;




<strong>Assignment Specifications</strong>

<strong> </strong>

You will develop a program that allows the user to play Montana according to the rules given above.  The program will use the instructor-supplied <strong>cards.py</strong> module to model the cards and deck of cards.  To help clarify the specifications, we provide a sample interaction with a program satisfying the specifications at the end of this document.




<ol>

 <li>The game will recognize the following commands (upper or lower case):</li>

</ol>




<table width="569">

 <tbody>

  <tr>

   <td width="192">            <strong>Sr Sc Dr Dc</strong></td>

   <td width="377">Source row &amp; column; Destination row &amp; column; all ints</td>

  </tr>

  <tr>

   <td width="192"><strong>     S          </strong></td>

   <td width="377">Shuffle Tableau (leaving sequences in place)</td>

  </tr>

  <tr>

   <td width="192">            <strong>Q</strong></td>

   <td width="377">Quit</td>

  </tr>

 </tbody>

</table>




where <strong>Sr </strong>and<strong> Dr</strong> denote row numbers (1 to 4); <strong>Sc </strong>and<strong> Dc </strong>denote column numbers (1 to 13).




The program will repeatedly display the current state of the game and prompt the user to enter a command until the user wins the game or enters “<strong>Q</strong>” (or “<strong>q</strong>”), whichever comes first.




The program will detect, report and recover from invalid commands.  The tableau will not be altered by an invalid command.




<ol start="2">

 <li>The program will use the following function to initialize a game:</li>

</ol>




<strong>initialize() </strong>Æ<strong> tableau </strong>




That function has no parameters.  It creates, initializes, and returns the tableau. This corresponds to the setup in the game rules:

<ul>

 <li>tableau is a list of 4 lists, each list containing 13 cards or empty spaces (aces). The first element of tableau is the leftmost column when displayed.</li>

</ul>




All cards are then dealt from the deck, left to right, one to each column of a thirteen-column tableau filling the top row first.




Note: we will use the whole deck of cards considering aces as empty spaces when displayed.




<ol start="3">

 <li>The program will use the following function to display the current state of the game:</li>

</ol>




<strong>display( tableau ) </strong>Æ<strong> None </strong>




Provided.




Note: aces are displayed as blank spaces.




<ol start="4">

 <li>The program will use the following function to determine if a requested move is valid:</li>

</ol>




<strong>validate_move(tableau,source_row,source_col,dest_row,dest_col) </strong>Æ<strong> Bool </strong>




That function has five parameters:  the data structure representing the tableau and four <strong>ints</strong> the source row &amp; column and the destination row &amp; column.  Row and column ints are in the ranges 0 &lt;= row &lt;= 3 and 0 &lt;= column &lt;= 12. The function will return <strong>True,</strong> if the move is valid; and <strong>False</strong>, otherwise.  A move is valid

<ul>

 <li>if the destination is empty (contains an ace)</li>

 <li>if the empty destination is the leftmost column and the source card has rank 2</li>

 <li>if the empty destination is not the leftmost column and the card to the left is the same suit as the source card and has a rank that is one less than the source card’s rank.</li>

</ul>




Hint: this kind of function is easiest to code with many return statements, sometimes returning True and sometimes returning False.  If some condition indicates that the move is valid or not, immediately return.  For example, if the destination isn’t empty (an ace), immediately return False.  Another way to think of it is to look for ways to return False and at the end have a “return True” if you got that far without returning False.




<ol start="5">

 <li>The program will use the following function to move a card within the tableau:</li>

</ol>




<strong>move(tableau,source_row,source_col,dest_row,dest_col) </strong>Æ<strong> Bool </strong>




That function has five parameters:  the data structure representing the tableau and four <strong>ints</strong> the source row &amp; column and the destination row &amp; column.  Row and column ints are in the ranges 0 &lt;= row &lt;= 3 and 0 &lt;= column &lt;= 12. If the move is valid, the function will update the tableau and return True; otherwise, it will do nothing to it and return False.




Hint: swap the source card with the destination card (an ace) so the source now becomes an empty space.




<ol start="6">

 <li>The program will use the following function to check if the game has been won:</li>

</ol>




<strong>check_win( tableau ) </strong>Æ<strong> Bool </strong>




That function has one parameter: the data structure representing the tableau.  The game is won when each row of the tableau is an increasing sequence of cards of the same suit starting with a 2 in the leftmost column up through a king in the next to last column with a blank space in the rightmost column (actually holding an ace that isn’t displayed, but the ace may be of any suit since it is simply representing a blank space).  Note that any suit may be in any row, but the entire row must be of the same suit.




Hint: this kind of function is easiest to code with many return statements, generally returning False if some condition isn’t met and returning True at the end, if there was never a False returned.




<ol start="7">

 <li>The program will use the following function to shuffle cards in the tableau</li>

</ol>




<strong>shuffle_tableau( tableau ) </strong>Æ<strong> None</strong>




(Note that this is the hardest part of the game and should only be implemented after the rest of the game is complete.)




Only some cards are shuffled: cards that are already in a same-suit sequence starting with a 2 in the leftmost column are left in place and not shuffled.  All other cards are shuffled and then dealt back into the tableau, but there will be one blank space in each row and it will be at the right end of the sequence that is left in place (or in the leftmost column, if there is no sequence in that row).  See example above in the description of the game.

<strong>Hint: First, you need to extract all the cards that needs to be shuffled including the aces and store them into a list. Then, shuffle the list. After that, remove all the aces from the list and distribute the aces into the tableau. Last step is to distribute the remaining cards into the tableau. </strong>




<ol start="11">

 <li>Once you write all your function, it is time to write your main function:</li>

 <li>Your program should start by initializing the tableau.</li>

 <li>Display the tableau.</li>

 <li>Ask to input an option and check the validity of the input.</li>

 <li>If ‘Q’, quit the game</li>

 <li>If ‘S’, shuffle the tableau and display the tableau</li>

 <li>If ‘<strong>Sr Sc Dr Dc</strong>’, move card from Tableau (Sr, Sc) to empty Tableau (Dr, Dc).</li>

 <li>If none of these options, the program should display an error message.</li>

 <li>The program should repeat until the user won or quit the game.</li>

 <li>Then ask if the user wants another game</li>

 <li>Display a goodbye message.</li>

</ol>







<strong>Assignment Notes </strong>




<ol>

 <li>Before you begin to write any code, play with the provided demo program and look over the sample interaction supplied on the project website to be sure you understand the rules of the game and how you will simulate the demo program. The demo program is at <a href="http://worldofsolitaire.com/">http://worldofsolitaire.com/</a><a href="http://worldofsolitaire.com/">:</a> Click on “Choose Game” at the top of the screen and click on “Montana”.</li>

</ol>




<ol start="2">

 <li>We provide a module called <strong>py</strong> that contains a Card class and a Deck class. Your program must use this module (<strong>import cards</strong>). <em>Do not modify this file!</em>  This is a generic module for any card game and happens to be implemented with “aces low” (having a rank of 1). Your game has blank spaces which we implement underneath with aces.  Your program must implement that <em>without modifying the</em> <strong>cards</strong> <em>module</em><strong>.</strong></li>

</ol>




<ol start="3">

 <li>Laboratory Exercise #11 demonstrates how to use the <strong>cards</strong> Understanding those programs should give you a good idea how you can use the module in your game.</li>

</ol>




<ol start="4">

 <li>We have provided a framework named <strong>py</strong> to get you started.</li>

</ol>

<em>Using this framework is mandatory</em>.  Begin by downloading <strong>proj10.py</strong>.  Check that it compiles.  Gradually replace the “stub” code (marked with comments) with your own code.  (Delete the stub code.)




<ol start="5">

 <li>The coding standard for CSE 231 is posted on the course website:         <a href="https://www.cse.msu.edu/%7Ecse231/General/coding.standard.html">http://www.cse.msu.edu/~cse231/General/coding.standard.html</a></li>

</ol>




Items 1-9 of the Coding Standard will be enforced for this project.




<ol start="6">

 <li>Your program may not use any global variables inside of functions. That is, all variables used in a function body must belong to the function’s local name space.  The only global references will be to functions and constants.</li>

</ol>




<ol start="7">

 <li>Your program may not use any nested functions. That is, you may not nest the definition of a function inside another function definition.</li>

</ol>




<ol start="8">

 <li>Your program must contain the functions listed above; you may develop additional functions, as appropriate.</li>

</ol>







<strong>TEST 1  (no shuffle) </strong>

Montana Solitaire.

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;      5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;  J&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 1 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 9 4 2

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




<a href="#_Toc53586">Enter choice:  (q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 13 3    10 </a>

<a href="#_Toc53587">      1   2   3   4   5   6   7   8   9  10  11  12                                        13  </a>

<a href="#_Toc53588">  1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;       2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;   3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  K&#x2665;  8&#x2665;  6&#x2665;   4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;                                                               </a>

<a href="#_Toc53589">Enter choice:  (q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 3 11 1    13 </a>

<a href="#_Toc53590">      1   2   3   4   5   6   7   8   9  10  11  12                                        13  </a>




1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;      8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 3 3 11

<h3><a name="_Toc53587"></a>      1   2   3   4   5   6   7   8   9  10  11  12  13</h3>

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;      J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 13 4 3

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




separated: source_row,source_col,dest_row,dest_col: 2 12 2 6

1   2   3   4   5   6   7   8   9  10  11  12  13

&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;

Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 9 4 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660;     10&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 10 2 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;      K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 4 2 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;     10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 11 4 4

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;      Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 11 1 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;      J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 12 4 13

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;      K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;      J&#x2665;  Q&#x2665;

separated: source_row,source_col,dest_row,dest_col: 2 11 1 12

1   2   3   4   5   6   7   8   9  10  11  12  13

&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  K&#x2660;  K&#x2666;      J&#x2665;  Q&#x2665;

Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 8 2 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;      K&#x2660;  K&#x2666;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 9 2 12

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;          K&#x2666;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 8 4 8

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;     10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  9&#x2660;      K&#x2666;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 3 12 2 8

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;      6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  9&#x2660;      K&#x2666;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 10 3 12

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  9&#x2660;              J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 9 4 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665;      J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;  9&#x2665;  8&#x2660;  9&#x2660; 10&#x2660;          J&#x2665;  Q&#x2665;

separated: source_row,source_col,dest_row,dest_col: 4 6 2 9

1   2   3   4   5   6   7   8   9  10  11  12  13

&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665;  9&#x2665;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;      8&#x2660;  9&#x2660; 10&#x2660;          J&#x2665;  Q&#x2665;

Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 10 4 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665;  9&#x2665;      Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665; 10&#x2665;      8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 5 2 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;          8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 3 13 4 5

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;      8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 7 4 6

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;      8&#x2665;  9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 7 2 7

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  8&#x2665;  9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;      9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 8 4 7

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;      9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2660; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 8 2 8




1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;  9&#x2665; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;     10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 9 4 8

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;     10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2660;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 9 2 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660; 10&#x2665;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665;      J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 10 4 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;      Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  J&#x2660;      J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 10 2 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;          J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 12 4 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  J&#x2665;          Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 4 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  J&#x2665;  Q&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 13 4 12

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;       4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665;  9&#x2665; 10&#x2665;  J&#x2665;  Q&#x2665;  K&#x2665;     You won!




Do you want to play again (y/n)?n Thank you for playing.

<strong>             </strong>

<strong>TEST 2  (with shuffle) </strong>




Montana Solitaire.

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;      5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;  J&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 1 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 9 4 2

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 13 3 10

1   2   3   4   5   6   7   8   9  10  11  12  13

<h2><a name="_Toc53588"></a>  1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;       2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;   3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  K&#x2665;  8&#x2665;  6&#x2665;   4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;</h2>




<h1><a name="_Toc53589"></a>Enter choice:</h1>

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 3 11 1 13

<h3><a name="_Toc53590"></a>      1   2   3   4   5   6   7   8   9  10  11  12  13</h3>

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;      8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 3 3 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;      J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 13 4 3

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 12 2 6

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  K&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  8&#x2665;  6&#x2665;

4:  2&#x2665;  3&#x2665;  4&#x2665;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;      K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;      7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;     10&#x2660;  K&#x2665;  K&#x2666;  5&#x2665;  K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;      8&#x2660;

4:  2&#x2665;  3&#x2665;  4&#x2665;      Q&#x2663;  Q&#x2665; 10&#x2665;  6&#x2665;  J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 5 1 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;     10&#x2660;  K&#x2665;  K&#x2666;  5&#x2665;  K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;      8&#x2660;

4:  2&#x2665;  3&#x2665;  4&#x2665;          Q&#x2665; 10&#x2665;  6&#x2665;  J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 10 3 12

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;     10&#x2660;  K&#x2665;      5&#x2665;  K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;  8&#x2660;

4:  2&#x2665;  3&#x2665;  4&#x2665;          Q&#x2665; 10&#x2665;  6&#x2665;  J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 3 13 2 7

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660; 10&#x2660;  K&#x2665;      5&#x2665;  K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;          Q&#x2665; 10&#x2665;  6&#x2665;  J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 11 4 4

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660; 10&#x2660;  K&#x2665;          K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;      Q&#x2665; 10&#x2665;  6&#x2665;  J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 8 4 5

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  7&#x2665;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660; 10&#x2660;  K&#x2665;          K&#x2663;  8&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  Q&#x2665; 10&#x2665;      J&#x2660;  K&#x2660;  J&#x2665;  9&#x2665;  9&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;      Q&#x2660;   2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;      7&#x2665;  8&#x2665;  J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;      9&#x2660; 10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665; 10&#x2660;  K&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 7 2 8

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;      Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;  7&#x2665;  8&#x2665;  J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;         10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665; 10&#x2660;  K&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 1 12

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;  7&#x2665;  8&#x2665;  J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;         10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665; 10&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 9 4 6

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;      8&#x2665;  J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;     10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665; 10&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 10 4 7

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660;          J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665; 10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665; 10&#x2660;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 12 2 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;      J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665; 10&#x2665;  J&#x2660;  9&#x2665;  K&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 9 2 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  J&#x2665;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665; 10&#x2665;      9&#x2665;  K&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 11 4 9

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;  Q&#x2660;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;      Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665; 10&#x2665;  J&#x2665;  9&#x2665;  K&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 13 2 11

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  Q&#x2663;  K&#x2663;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;  7&#x2660;  8&#x2660;  9&#x2660; 10&#x2660;  J&#x2660;  Q&#x2660;  Q&#x2665;  K&#x2660;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;  J&#x2666;  Q&#x2666;  K&#x2666;

4:  2&#x2665;  3&#x2665;  4&#x2665;  5&#x2665;  6&#x2665;  7&#x2665;  8&#x2665; 10&#x2665;  J&#x2665;  9&#x2665;  K&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s No more shuffles remain.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: q

Do you want to play again (y/n)?n Thank you for playing.

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong>             </strong>

<strong>TEST 3 (error checking) </strong>




Montana Solitaire.

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;      5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;  J&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col:  Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: a Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 a 3 4 Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1.5 2 3 13

Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2336 Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 2 2 3 Error: invalid move.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 3 10

Error: invalid move.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 6 10 2 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 0 10 2 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 0 2 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 14 2 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 6 0 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 6 5 6 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 6 2 0 Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 2 6 2 14

Error: row and/or column out of range. Please Try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 1 1 1 1 Error: invalid move.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 4 13 Error: invalid move.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: 4 13 1 10

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;  5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;      K&#x2660;  9&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      Q&#x2663;  Q&#x2660;  K&#x2663;  Q&#x2665;  7&#x2660;  K&#x2666; 10&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      4&#x2665;  5&#x2665; 10&#x2660;

4:  2&#x2665;      8&#x2660;  J&#x2666;  J&#x2660;  Q&#x2666;  8&#x2665;  K&#x2665;  3&#x2665;  9&#x2660;  J&#x2665;  6&#x2665;  7&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;  J&#x2663;      Q&#x2663;  Q&#x2665;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      Q&#x2666;  K&#x2660;  K&#x2665;  J&#x2660; 10&#x2665;  8&#x2660;  7&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      J&#x2665;  9&#x2665;  9&#x2660;

4:  2&#x2665;      K&#x2666;  6&#x2665;  Q&#x2660;  3&#x2665;  7&#x2660;  J&#x2666; 10&#x2660;  4&#x2665;  K&#x2663;  5&#x2665;  8&#x2665;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: s No more shuffles remain.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: a Error: invalid input.  Please try again.




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: q




Do you want to play again (y/n)?y

Montana Solitaire.

1   2   3   4   5   6   7   8   9  10  11  12  13

1:  2&#x2663;  3&#x2663;  4&#x2663;  5&#x2663;  6&#x2663;  7&#x2663;  8&#x2663;  9&#x2663; 10&#x2663;      5&#x2665;  Q&#x2665;  J&#x2666;

2:  2&#x2660;  3&#x2660;  4&#x2660;  5&#x2660;  6&#x2660;      7&#x2665;  9&#x2660;  K&#x2660; 10&#x2660;  K&#x2663;  7&#x2660;  4&#x2665;

3:  2&#x2666;  3&#x2666;  4&#x2666;  5&#x2666;  6&#x2666;  7&#x2666;  8&#x2666;  9&#x2666; 10&#x2666;      K&#x2665;  8&#x2665;  6&#x2665;

4:  2&#x2665;      Q&#x2666;  J&#x2660; 10&#x2665;  9&#x2665;  8&#x2660;  Q&#x2660;  3&#x2665;  K&#x2666;  Q&#x2663;  J&#x2665;  J&#x2663;




Enter choice:

(q)uit, (s)huffle, or space-separated: source_row,source_col,dest_row,dest_col: q




Do you want to play again (y/n)?n Thank you for playing.










<strong>Grading Rubric </strong>




Computer Project #10

Scoring Summary




General Requirements:

(5 pts)         Coding Standard 1-9

(descriptive comments, mnemonic identifiers, format, etc…)







Implementations:




<ul>

 <li>pts) initialize</li>

 <li>pts) validate_move</li>

</ul>

(8 pts) move

-3 for Boolean return

-5 for Tableau update

(8 pts) check_win

(8 pts) shuffle_tableau

(6 pts) Test 1 (6 pts) Test 2

(4 pts) Test 3

<strong> </strong>




<strong>  </strong>

<strong> </strong>