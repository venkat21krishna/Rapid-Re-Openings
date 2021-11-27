# Rapid-Re-Openings

#include<bits/stdc++.h>
using namespace std;
#define ll long long
#define fo(i,n) for(int i = 0; i < n; i++)
#define rep(i,a,b) for(int i = a; i <= b; i++)
#define vi vector<int>
#define pi pair<int>
#define pb push_back
int a, b, c, x, y, z, n, t;

void solve() {
    ll n; 
    cin>>n;
    vector<ll> v,ans;
    ll x;
    map<ll,ll> mp,ch;
    for(ll i=0; i < 2*n; i++)
    {
        cin>>x;
        v.pb(x);
        if(mp[x]==0) ans.pb(x);
        mp[x]++;
    }
    sort(ans.begin(),ans.end());
    ll k=0;
    ch[ans[0]]++;
    for (ll i = 1; i < ans.size(); i++)
    {
        ll temp = ceil((i+1)/2.0);
        ch[ans[temp-1]]++;
    }
    k = ans.size()-1; ch[ans[k]]++;

    for (ll i = k-1; i >= 0; i--)
    {
        ll temp;
        temp = i+ceil((k-i+1)/2.0);
        ch[ans[temp-1]]++;
    }
    
    for (auto i = mp.begin(),j=ch.begin(); i != mp.end(); i++,j++)
    {
        if(*i!=*j)
        {
            cout << "-1\n";
            return;
        }
    }

    for(int i=0;i<ans.size();i++)
    {
        cout << ans[i] << ' ';
    }
    
}

int main() {
    int t;
    cin>>t;
    while(t--) {
        solve();
    }
    return 0;
}
