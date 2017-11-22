# 朋友

Misaka 有 20002 位妹妹，由於妹妹太多了，彼此之間的關係十分的生疏，因此 Misaka 想要調查一下妹妹之間的友情關係。

由於妹妹們平時忙於進行實驗，現在只有N位妹妹可供調查，編號依序由0號到N-1號，Misaka 接下來會調查兩個妹妹的關係，如果妹妹a與妹妹b互為朋友，那妹妹a的朋友與妹妹b的朋友彼此間也都會是朋友。

現在提供了一些 Misaka 的調查資料，你能判斷兩個任妹妹是不是朋友嗎？

本題目有提供模板於下

```cpp
#include<stdio.h>
#include<stdbool.h>
#define MAXN 2005

bool f[MAXN][MAXN];
int n;
void init(){
	int i=0,j;
	for(;i<n;++i){
		for(j=0;j<n;++j){
			f[i][j]=false;
		}
		f[i][i]=true;
	}
}
bool is_friend(int a,int b){
	//如果f[a][b]=true，就表示他們是朋友
	//你的作業就是要好好維護f陣列
	return f[a][b];
}
int ga[MAXN],gb[MAXN];
int len_ga,len_gb;
void get_ga(int a){
	//ga陣列存是a的所有朋友
	//例如a的朋友有： 1, 4, 5, 10
	//那ga[]={1,4,5,10}, len_ga=4
	//請思考要怎麼從f陣列得到ga
}
void get_gb(int b){
	//gb陣列存是b的所有朋友
	//和ga類似
}
void set_friend_ab(){
	//現在ga、gb你都有了
	//因為a和b會成為朋友，你要怎麼利用ga,gb來維護新的f陣列呢？
}
void merge_friend(int a,int b){
	if(is_friend(a,b)) return;
	get_ga(a);
	get_gb(b);
	set_friend_ab();
}
int main(){
	int t,q;
	scanf("%d",&t);
	while(t--){
		scanf("%d%d",&n,&q);
		init();
		while(q--){
			int op,a,b;
			scanf("%d%d%d",&op,&a,&b);
			if(op==1) puts(is_friend(a,b) ? "they are friends!" : "they are not friends!");
			else merge_friend(a,b);
		}
	}
	return 0;
}
```

# 輸入說明

第一行有一個數字t，表示有t筆測資。接下來每筆測資第一行有兩個數字N,Q，表示有N位妹妹接受調查，接下來有Q個指令。每個指令由3個數字P,a,b組成，若P等於0，則表示編號a,b的妹妹互為朋友。若P等於1，則根據已知的線索，判斷妹妹a，妹妹b彼此間是否為朋友。0<=a,b<N , a!=b

0<Q<=10^5
0<N<=2000
# 輸出說明

對於每一個P=1的指令，若a,b互為朋友請輸出```they are friends!```，否則輸出```they are not friends!```，輸出完後請換行。

# 範例輸入

```
1
5 7
1 0 1
0 0 1
1 0 1
1 2 4
0 2 3
0 3 4
1 2 4
```

# 範例輸出

```
they are not friends!
they are friends!
they are not friends!
they are friends!
```
