# 자금관리 💰

개인 자금 관리 앱 — Firebase 실시간 동기화 + PWA

## 배포 방법

### 1. Firebase 프로젝트 설정

Firebase 콘솔(https://console.firebase.google.com)에서:

1. **Firestore Database** 생성 (프로덕션 모드)
2. **Firestore 보안 규칙** 변경:
   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /appdata/{syncCode} {
         allow read, write: if true;
       }
     }
   }
   ```
3. **Hosting** 활성화

### 2. `.firebaserc` 수정

```json
{
  cd /tmp/MONEY
# YOUR_PROJECT_ID를 실제 Firebase 프로젝트 ID로 교체
  }
}
```

### 3. 배포

```bash
npm install -g firebase-tools
firebase login
cd /tmp/MONEY
firebase deploy --only hosting
```

### 4. 앱 사용

1. 배포된 URL 접속
2. Firebase 콘솔에서 `firebaseConfig` 복사 → 앱에 붙여넣기 (최초 1회)
3. 동기화 코드 설정 (모든 기기에서 같은 코드 사용)
4. PIN 설정 후 사용

## 모바일 설치 (iPhone)

Safari로 접속 → 공유 버튼 → "홈 화면에 추가"
