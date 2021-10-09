# 132-leetcode-456


class Solution {
public:
    bool find132pattern(vector<int>& nums) {
       int n = nums.size();
        if (n < 3) 
            return false;
        
        int minno[n];
        minno[0] = nums[0];
        for (int i = 1; i < n; i++)
            minno[i] = min(nums[i], minno[i - 1]);
        
        stack<int> s;
        for (int j = n - 1; j >= 0; j--) 
        {
            while (!s.empty() && s.top() < nums[j]) 
            {
                if (s.top() > minno[j])
                    return true;
                s.pop();
            }
            s.push(nums[j]);
        }
        return false;
    
    }
};
