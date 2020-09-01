# myproject
parsing
// bank.cpp : Defines the entry point for the console application.
//

#include "stdafx.h"
#include<iostream>
using namespace std;
class Bank
{
	private :
		int acno;
		char name[40];
		long balance;
		
	public :
	
	Bank()
	{
		cout<<"obj is created";
		
	}
	
	void openaccount()	
	{
		cout<<"\nenter account num : ";
		cin>>acno;
		cout<<"\nenter name : ";
		cin>>name;
		cout<<"\nenter balance : ";
		cin>>balance;
	}
	
	void showaccount()
	{
		cout<<"\naccount number : "<<acno;
		cout<<"\name : "<<name;
		cout<<"\nbalance : "<<balance;
	}
	
	void deposite()
	{
		long amount;
		cout<<"\nenter the amount to deposit : ";
		cin>>amount;
		balance=balance+amount;
		cout<<"\nthe total balance after seposition is : "<<balance;
	}
	
	void withdrawl()
	{
		long amount;
		cout<<"\nenter the amount for withdrawl : ";
		cin>>amount;
		
		if(amount<=balance)
		{
			balance=balance-amount;
			cout<<"\nthe total balance after reduction is : "<<balance;
		}
		if(amount>balance)
		{
			balance=balance-amount;
			cout<<"\nthe amount is in negatives because of in sufficient balance ."<<balance;
		}
		
	}
	
	int searchaccount(int a)
	{
		if (acno==a)
		{
			showaccount();
			return(1);
		}
		else
		{
			cout<<"\naccount not found : "<<endl;
		}
	return(0);	
	}
};

int _tmain(int argc, _TCHAR* argv[])
{
	Bank c[10];     //array type object of the class bank
	int i,ch,a,found=0;
	
	do
	{
		cout<<"\n0:for creating  acount";
		cout<<"\n1:display all accounts\n2:by account number\n3:deposit\n4:withdrawl\n5:exit "; //display all the options in program
		
		cout<<"\nplease now enter your choice : ";  //user input according to demand
		cin>>ch;
		
		switch (ch)
		{
		case 0:
			{

				for(int i=0; i<1; i++)
				c[i].openaccount();
			}
			break;
		 case 1: //display all accounts informations
		 for(i=0;i<1;i++)
		 {
		   c[i].showaccount();
		 }
		 break;
	
	     case 2: //search the account be account number
	     cout<<"\nenter the account num : ";
		 cin>>a;
		 for(i=0;i<=2;i++) 
		 {
		   found=c[i].searchaccount(a);
		   if (found)	
		   break;
	     }
	     if (!found)
	        cout<<"\nfunction doesnot exists.";
	        break;
	
	     case 3: //deposit amount in the account
	     cout<<"\nenter the account number to deposit the amount in : ";
	     cin>>a;
	    
	     for(i=0;i<=2;i++)
	     {
	       found=c[i].searchaccount(a);
	       if (found)
	       {
		   c[i].deposite();
		   break ;
	       }
	     }
	
	     if(!found)
	     cout<<"\nacount not found so cant deposite. ";
	     break ;
	
	    
	     case 4 : //withdrwal of amount from the account.
	     cout<<"\nenter the account number to with drawl amount from : ";
	     cin>>a;
	     for(i=0;i<=2;i++)
	     {
	    	found=c[i].searchaccount(a);
	    	if(found)
	    	{
	    		c[i].withdrawl();
	    		break;
			}
		 }
			if(!found)
			cout<<"account not found so amount cant be withdrawl ";
			break;
		
	     case 5 : //exits the function
	     cout<<"\nhave a good day . anneyong! "<<endl;
	     break;
	    
	     default : 
	     cout<<"\nwrong option :( "<<endl;
	   }
}
while(ch!=5);

system("pause");
return 0;
}
