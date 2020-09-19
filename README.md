# Sudoku solver
An application that solves sudokus, implemented with Javascript. Not brute-force style but one number at a time with different algorithms.

## Background
I created this application in high school, without proper software development training and totally ignorant of all good programming practises. It obviously has major problems. The reason that this kind of code ever sees the daylight and goes public is that I'm pretty impressed about 16-year-old me. This actually solves sudokus and even difficult ones (not the most extreme ones, though).

## Installation/Usage
Just open the html-file in a browser. Tested with Chrome v. 85.

Options "Näytä mahdolliset" and "Tyhjennä mahdolliset" are for debugging purposes.

## Solution overview
As a remainder, here are the basic sudoku rules:

Each number (1 - 9) can exist only once on each:
1. row
1. column
1. 3x3 square

The solution is built on 3D-array called "mahdolliset" with dimensions 9 x 9 x 10. Two first dimensions represent the sudoku board (9 x 9 cells) and the last is for each possible number that can exists in that cell (index 0 is not used, then 9 numbers). For example,
    
    mahdolliset[0][0][2] = 1

means that the cell in the upper-left corner can contain number 2 (value would be 0 if it cannot).

First, the possible numbers in each cell are reduced based on the current numbers on the sudoku board using the basic sudoku rules. Then more complex algorithms are applied. In the end, the mahdolliset-array is looped through to check if there is only one possible number on each row, column and 3x3-square. If there is, that specific number is added on the sudoku board and the process started from the start.