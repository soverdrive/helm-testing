## to update helm repo

https://www.opcito.com/blogs/creating-helm-repository-using-github-pages

## list of argoCD commands

### adding github repo to argoCD to be listened
argocd repo add https://github.com/soverdrive/helm-testing.git --username placeholder --password xxx

https://argo-cd.readthedocs.io/en/stable/user-guide/private-repositories/

### adding sample app
argocd app create everywhere --project default --repo https://github.com/soverdrive/helm-testing.git --path ./result --dest-namespace default --dest-server https://kubernetes.default.svc --sync-policy auto --upsert

### adding secret
argocd app create everywhere-secret --project default --repo https://github.com/soverdrive/helm-testing.git --path ./secrets --dest-namespace default --dest-server https://kubernetes.default.svc --sync-policy auto --upsert

kubeseal -f rawsecret/testing-secret.yaml -w secrets/testing-secret-sealed.yaml --name testing-secret
