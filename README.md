# bookdetails
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct library
{
  char bookname[30];
  char auname[25];
  int year,price;
  float version;
};

int main()
{
struct library l[20];
char arNm[30], bookNm[30], t[20];
int i, j, n, yr,temp,te;
i = j = 0;
printf("/*How Many Details You Want to Add*/\n\nEnter Limit : ");
scanf("%d",&n);
printf("------------------------------------------\n");
for(i=0;i<n;i++)
{
printf("\tEnter Details of Book-%d",i+1);
printf("\n------------------------------------------\n");
printf("Book Name\t\t: ");
scanf("%s",l[i].bookname);
printf("Author Name\t\t\t: ");
scanf("%s",l[i].auname);
printf("version\t\t\t: ");
scanf("%f",&l[i].version);
printf("Publication year\t\t: ");
scanf("%d",&l[i].year);
printf("Cost         : ");
scanf("%d",&l[i].price);

printf("------------------------------------------\n");
}

  while (j != 6)
  {
    printf("1. List all books of given author\n");
    printf("2. List the books in increasing order of price\n");
    printf("3. List the books in given year\n");
    printf("4. List the books in increasing order of author");
    printf("5. List the books in increasing order of year\n");
    printf("6. Exit");
    printf("\n\nEnter one of the above : ");
    scanf("%d", &j);

    switch (j)
    {

    case 1:
      printf("Enter author name : ");
      scanf("%s", arNm);
      for(i=0;i<n;i++)
      {

	if(strcmp(arNm,l[i].auname)==0)
	  printf("%s %s %d %d %f", l[i].bookname, l[i].auname, &l[i].price, &l[i].year, &l[i].version);
	else
	  printf("Not found");
      }

      break;
    case 2:
     for (i = 0; i < n - 1; i++)
      {
	for (j = 0; j < (n - 1-i); j++)
	{
	    if (l[j].price < l[j + 1].price)
	    {
		temp = l[j].price;
		l[j].price = l[j + 1].price;
		l[j + 1].price = temp;
	    }
	}
    }
     printf(".........Details......");
     for(i=0;i<=n;i++)
     printf("%s %s %d %d %f", l[i].bookname, l[i].auname, &l[i].price, &l[i].year, &l[i].version);
      break;

    case 3:
      printf("Enter year : ");
      scanf("%s", yr);
      for (i = 0; i < n; i++)
      {
        
	if (yr==l[i].year)
	  printf("%s %s %d %d %f", l[i].bookname, l[i].auname, &l[i].price, &l[i].year, &l[i].version);

      }
      break;

    case 4:
      for(i=0;i<=n;i++)
      for(j=i+1;j<=n;j++){
	 if(strcmp(l[i].auname[i],l[i].auname[j])>0){
	    strcpy(t,l[i].auname[i]);
	    strcpy(l[i].auname[i],l[i].auname[j]);
	    strcpy(l[i].auname[j],t);
         }
      }
   printf("Order of Sorted Names and details:");
   for(i=0;i<=n;i++)
     printf("%s %s %d %d %f", l[i].bookname, l[i].auname, &l[i].price, &l[i].year, &l[i].version);
    break;

    case 5:
      for (i = 0; i < n - 1; i++)
      {
	for (j = 0; j < (n - 1-i); j++)
        {
            if (l[j].year < l[j + 1].year)
            {
		te = l[j].year;
		l[j].year = l[j + 1].year;
		l[j + 1].year = te;
            } 
        }
    }
    printf(".........Details......");
     for(i=0;i<=n;i++)
     printf("%s %s %d %d %f", l[i].bookname, l[i].auname, &l[i].price, &l[i].year, &l[i].version);
      break;
    case 6:
      exit(0);
    }
  }
  return 0;
}
