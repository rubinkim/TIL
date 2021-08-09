```python
#DFS로 특정 노드를 방문하고 연결된 모든 노드들도 방문한다
def dfs(x, y):
    # 주어진 범위를 벗어나는 경우에는 즉시 종료한다
    if x <= -1 or x >= n or y <= -1 or y >= m:
        return False
    if graph[x][y] == 0:         # 현재 노드를 아직 방문하지 않았다면
        graph[x][y] = 1
        # 현재 노드의 상하좌우에 위치한 모든 노드들도 재귀적으로 호출한다
        dfs(x-1, y)
        dfs(x+1, y)
        dfs(x, y-1)
        dfs(x, y+1)
        return True
    return False        # 현재 노드값이 1이라면 False를 반환한다
```

```python
# N, M을  공백을 기준으로 구분하여 입력을 받는다
n, m = map(int, input().split())

# 2차원 리스트의 맵정보를 입력받는다.
graph = []
for i in range(n):
    graph.append(list(map(int, input())))
    
# 모든 노드(위치)에 대하여 음료수를 채운다.
result = 0
for i in range(n):
    for k in range(m):
        if dfs(i,k) == True: #현재 노드에서 dfs를 수행했는데 값이 0인 상태로 미방문 상태
            result += 1
            
print(result)
            
```

