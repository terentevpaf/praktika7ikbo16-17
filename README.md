# praktika7ikbo16-17
# Терентьев Павел Вадимович ИКБО-16-17

<pre>
import java.util.Scanner;
import java.util.ArrayDeque;

public class Main {

    public static void game(int player1[], int player2[]){
        String res = "";
        ArrayDeque<Integer> plFirst = new ArrayDeque<Integer>();
        ArrayDeque<Integer> plSecond = new ArrayDeque<Integer>();
        for(int i = 0; i < 5; i++)
        {
            plFirst.add(player1[i]);
            plSecond.add(player2[i]);
        }

        int index = 0;
        int plFirstSize = plFirst.size();
        int plFCard = 0;
        int plSCard = 0;
        while(plFirstSize > 0 && plFirstSize < 10)
        {
            plFCard = (int) plFirst.pop();
            plSCard = (int) plSecond.pop();
            if((plFCard == 0 && plSCard == 9) || (plFCard > plSCard && plFCard != 9 && plSCard != 0))
            {
                plFirst.addLast(plFCard);
                plFirst.addLast(plSCard);
            }
            else if((plFCard == 9 && plSCard == 0) || (plFCard < plSCard && plFCard != 0 && plSCard != 9))
            {
                plSecond.addLast(plFCard);
                plSecond.addLast(plSCard);
            }
            if(index == 106)
            {
                System.out.println("botva");
                break;
            }
            index++;
            plFirstSize = plFirst.size();
        }

        if(index != 106) {
            if (plFirst.size() == 0)
            {
                System.out.println("Победил второй игрок, количестко ходов: " + index);
            }
            else
            {
                System.out.println("Победил первый игрок, количестко ходов: " + index);
            }
        }
    }

    public static int[] EnterCards(int player)
    {
        String namePlayer = "Первый";
        String namePlayerDop = "Первого";
        if(player == 2)
        {
            namePlayer = "Второй";
            namePlayerDop = "Второго";
        }
        System.out.println(namePlayer + " игрок. Введите пять карт от 0 до 9:");

        Scanner in = new Scanner(System.in);
        int[] nums = new int[5];
        for(int i=0;i < nums.length; i++){
            nums[i]=in.nextInt();
        }

        System.out.print("Карты " + namePlayerDop + " игрока: ");

        for(int i=0;i < nums.length; i++){
            System.out.print(nums[i] + " ");
        }
        System.out.println();

        return nums;
    }

    public static void main(String[] args) {

        int[] nums1 = new int[5];
        int[] nums2 = new int[5];
        nums1 = EnterCards(1);
        nums2 = EnterCards(2);

        game(nums1, nums2);
    }
}
</pre>
