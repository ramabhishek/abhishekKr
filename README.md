# abhishekKr
rock paper scissor
package com.example.abhishek;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);


    }

    public void startGame_SinglePlayer(View view) {
        Intent i = new Intent(this, GameActivity.class);
        startActivity(i);

    }
    public void startGame_multiPlayer(View view) {
        Intent i = new Intent(this, MultiActivity.class);
        startActivity(i);

    }
    public void about(View view) {
        Intent i = new Intent(this, aboutActivity.class);
        startActivity(i);


    }


    }

------------------------

package com.example.abhishek;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;

import java.util.Random;

public class GameActivity extends AppCompatActivity {

    Button b_rock, b_scissor, b_paper;
    TextView tv_score;
    ImageView iv_ComputerChoice, iv_HumanChoice;

    int HumanScore,ComputerScore = 0;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_game);

        b_paper = (Button) findViewById(R.id.b_paper);
        b_scissor = (Button) findViewById(R.id.b_scissor);
        b_rock = (Button) findViewById(R.id.b_rock);

        iv_ComputerChoice = (ImageView) findViewById(R.id.iv_ComputerChoice);
        iv_HumanChoice = (ImageView) findViewById(R.id.iv_HumanChoice);

        tv_score = (TextView) findViewById(R.id.tv_score);

        b_paper.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.paper);
                String message = play_turn("paper");
                Toast.makeText(GameActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN : " +Integer.toString(HumanScore) +" || COMPUTER : "+Integer.toString(ComputerScore));

            }


        });

        b_rock.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.rock);
                String message = play_turn("rock");
                Toast.makeText(GameActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN : " +Integer.toString(HumanScore) +" || COMPUTER : "+Integer.toString(ComputerScore));




            }


        });

        b_scissor.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                iv_HumanChoice.setImageResource(R.drawable.scissor);
                String message = play_turn("scissor");
                Toast.makeText(GameActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE HUMAN : " +Integer.toString(HumanScore) +" || COMPUTER : "+Integer.toString(ComputerScore));

            }


        });


    }

    public String play_turn( String player_choice ){

        String computer_choice="";
        Random r=new Random();


        int computer_choice_number = r.nextInt(3)+1;
        if (computer_choice_number==1){
            computer_choice="rock";
        }else

        if (computer_choice_number==2) {
            computer_choice="scissor";
        }else

        if (computer_choice_number==3) {
            computer_choice="paper";
        }

        if (computer_choice=="rock") {
            iv_ComputerChoice.setImageResource(R.drawable.rock);

        } else

        if (computer_choice=="scissor") {
            iv_ComputerChoice.setImageResource(R.drawable.scissor);

        } else

        if (computer_choice=="paper") {
            iv_ComputerChoice.setImageResource(R.drawable.paper);

        }




        if(computer_choice== player_choice) {
            return " It's a TIE " ;
        }
        else if (player_choice =="scissor" && computer_choice == "rock") {
            ComputerScore++;
            return "Rock crushes scissors. Computer Wins!!!";

        }
        else if (player_choice =="scissor" && computer_choice == "paper") {
            HumanScore++;
            return "Scissor cuts Paper. You Win!!!";

        }

        else if (player_choice =="rock" && computer_choice == "scissor") {
            HumanScore++;
            return "Rock crushes scissors. You Win!!!";

        }

        else if (player_choice =="rock" && computer_choice == "paper") {
            ComputerScore++;
            return "Paper covers Rock . Computer Wins!!!";

        }
        else if (player_choice =="paper" && computer_choice == "rock") {
            HumanScore++;
            return "Paper covers Rock. You Win!!!";

        }
        else if (player_choice =="paper" && computer_choice == "scissor") {
            ComputerScore++;
            return "Scissor cuts Paper. Computer Wins!!!";

        }
        else return "don't know";
    }

}





------------------------------




package com.example.abhishek;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;

import java.util.Random;

public class MultiActivity extends AppCompatActivity {


    Button b_play;
    Button b_play2;
    TextView tv_score;
    ImageView iv_player1choice, iv_player2choice;

    int player1Score, player2Score = 0;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_multi);

        b_play = (Button) findViewById(R.id.b_play);
        b_play2 = (Button) findViewById(R.id.b_play2);

        iv_player1choice = (ImageView) findViewById(R.id.iv_player1Choice);
        iv_player2choice = (ImageView) findViewById(R.id.iv_player2Choice);

        tv_score = (TextView) findViewById(R.id.tv_score);


        b_play.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String player1Choice = "";
                Random r = new Random();


                int player1Choice_number = r.nextInt(3) + 1;
                if (player1Choice_number == 1) {
                    player1Choice = "rock";
                } else if (player1Choice_number == 2) {
                    player1Choice = "scissor";
                } else if (player1Choice_number == 3) {
                    player1Choice = "paper";
                }

                if (player1Choice == "rock") {
                    iv_player1choice.setImageResource(R.drawable.rock);

                } else if (player1Choice == "scissor") {
                    iv_player1choice.setImageResource(R.drawable.scissor);

                } else if (player1Choice == "paper") {
                    iv_player1choice.setImageResource(R.drawable.paper);

                }

                String message = play_turn("paper", "rock", "scissor");
                Toast.makeText(MultiActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE PLAYER1: " +Integer.toString(player1Score) +" || PLAYER2: "+Integer.toString(player2Score));


            }



        });


        b_play2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                String player2Choice = "";
                Random r = new Random();


                int player2Choice_number = r.nextInt(3) + 1;
                if (player2Choice_number == 1) {
                    player2Choice = "rock";
                } else if (player2Choice_number == 2) {
                    player2Choice = "scissor";
                } else if (player2Choice_number == 3) {
                    player2Choice = "paper";
                }

                if (player2Choice == "rock") {
                    iv_player2choice.setImageResource(R.drawable.rock);

                } else if (player2Choice == "scissor") {
                    iv_player2choice.setImageResource(R.drawable.scissor);

                } else if (player2Choice == "paper") {
                    iv_player2choice.setImageResource(R.drawable.paper);

                }

                String message = play_turn("paper", "rock", "scissor");
                Toast.makeText(MultiActivity.this, message, Toast.LENGTH_SHORT).show();
                tv_score.setText("SCORE PLAYER1: " +Integer.toString(player1Score) +" || PLAYER2: "+Integer.toString(player2Score));



            }
        });


    }

    private String play_turn(String paper, String rock, String scissor) {



        String player1choice="";

        String player2choice = "";
        if (player1choice == player2choice) {
            return "a better player wins the game";
        }
          else if (player1choice == "scissor" && player2choice == "paper") {
            player1Score++;
            return "Scissor cuts Paper. You Win!!!";

        } else if (player1choice == "rock" && player2choice == "scissor") {
            player1Score++;
            return "Rock crushes scissors. You Win!!!";

        } else if (player1choice == "rock" && player2choice == "paper") {
            player2Score++;
            return "Paper covers Rock . Computer Wins!!!";

        } else if (player1choice == "paper" && player2choice == "rock") {
            player1Score++;
            return "Paper covers Rock. You Win!!!";

        } else if (player1choice == "paper" && player2choice == "scissor") {
            player2Score++;
            return "Scissor cuts Paper. Computer Wins!!!";

        } else return "don't know";
    }

}




















