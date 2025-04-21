# 📝 Next.js App Setup & Notes

## 🚀 Create a New Project
```bash
npx create-next-app@latest
# or use `.` if you want to create it in the current folder
```

## 📦 Setup Options
| Option | Choice |
|--------|--------|
| Project Name | `my-app` or `.` for current folder |
| TypeScript | ❌ No |
| ESLint | ✅ Yes |
| Tailwind CSS | ✅ Yes |
| Use `src/` directory | ❌ No |
| Use App Router | ✅ Yes (Recommended) |
| Import Alias | ❌ No customization |

---

## 📁 Folder Structure (Inside `app`)

| File / Folder | Purpose |
|---------------|---------|
| `page.js` | Default route content |
| `layout.js` | Page structure |
| `error.js` | Global error page |
| `not-found.js` | Global 404 page |
| `loading.js` | Global loading UI |
| `icon.png` | Website favicon |
| `global.css` | Global CSS |

> 🔄 Every folder in `app/` is treated as a route.  
> 📁 Nested folders = Nested Routes

---

## 🧩 Components & Pages

- All folders under `app/` are treated as routes.
- Any `js/jsx` file other than `page.js` is considered a **component**.
- Components should be outside the `app/` folder (best practice).
- Component names should start with a **capital letter**.
- Function names don't matter in `page.js`.

---

## ⚠️ Special Notes

- `error.js` is a **client component** – must add `"use client"`.
- Hooks (like `useState`, `useEffect`) **cannot be used** in server components.
- Add `"use client"` at the top if you need hooks.
- For `<Image />`, use `fill` if you don't know exact dimensions.
- `async/await` is **only for server components**.

---

## 🔄 Special Files in Each Route Folder

| File | Use |
|------|-----|
| `loading.js` | Loading UI per route |
| `error.js` | Error UI per route |
| `not-found.js` | 404 UI per route |

---

## 📂 `lib/` Folder – Data Fetching Helper

Example: Fetching local JSON

```js
// lib/getAllCompanies.js
import fsPromises from 'fs/promises';
import path from 'path';

async function getAllCompanies() {
  const filePath = path.join(process.cwd(), '/public/Companies.json');
  const jsonData = await fsPromises.readFile(filePath);
  const objectData = JSON.parse(jsonData);

  return objectData;
}

export default getAllCompanies;
```

> 📂 `lib/` is not a reserved name – it's used conventionally.

---

## ⚡ `useOptimistic` – For Instant UI Update

- Ideal for buttons or UI that needs to update immediately.
- Helpful for optimistic UI feedback.

🧠 **Read more**:  
[New React Updates Using useOptimistic Hook in a NextJS App – dev.to](https://dev.to/powdree123/new-react-updates-using-useoptimistic-hook-in-a-nextjs-app-3fc9)
